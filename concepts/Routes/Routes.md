# Routes
### Overview

The most basic feature of any web application is the ability to interpret a request sent to a URL, then send back a response.  In order to do this, your application has to be able to distinguish one URL from another.

Like most web frameworks, Sails provides a router: a mechanism for mapping URLs to controllers and views.  **Routes** are rules that tell Sails what to do when faced with an incoming request.  There are two main types of routes in Sails: **custom** (or "explicit") and **automatic** (or "implicit").


### Custom Routes

Sails lets you design your app's URLs in any way you like- there are no framework restrictions.

Every Sails project comes with [`config/routes.js`](http://beta.sailsjs.org/#/documentation/reference/sails.config/sails.config.routes.html), a simple [Node.js module](http://nodejs.org/api/modules.html) that exports an object of custom, or "explicit" **routes**. For example, this `routes.js` file defines six routes; some of them point to a controller's action, while others route directly to a view.

```javascript
// config/routes.js
module.exports = {
  'get /signup': { view: 'conversion/signup' },
  'post /signup': 'AuthController.processSignup',
  'get /login': { view: 'portal/login' },
  'post /login': 'AuthController.processLogin',
  '/logout': 'AuthController.logout',
  'get /me': 'UserController.profile'
}
```


Each **route** consists of an **address** (on the left, e.g. `'get /me'`) and a **target** (on the right, e.g. `'UserController.profile'`)  The **address** is a URL path and (optionally) a specific [HTTP method](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods). The **target** can be defined a number of different ways ([see the expanded concepts section on the subject](http://beta.sailsjs.org/#/documentation/concepts/Routes/RouteTargetSyntax.html)), but the two different syntaxes above are the most common.  When Sails receives an incoming request, it checks the **address** of all custom routes for matches.  If a matching route is found, the request is then passed to its **target**.

For example, we might read `'get /me': 'UserController.profile'` as:

> "Hey Sails, when you receive a GET request to `http://mydomain.com/me`, run the `profile` action of `UserController`, would'ya?"

What if I want to change the view layout within the route itself?  No problem we could:

```javascript
'get /privacy': {
    view: 'users/privacy',
    locals: {
      layout: 'users'
    }
  },
```

#### Notes
+ Just because a request matches a route address doesn't necessarily mean it will be passed to that route's target _directly_.  For instance, HTTP requests will usually pass through some [middleware](http://beta.sailsjs.org/#/documentation/concepts/Middleware) first.  And if the route points to a controller [action](http://beta.sailsjs.org/#/documentation/concepts/Controllers?q=actions), the request will need to pass through any configured [policies](http://beta.sailsjs.org/#/documentation/concepts/Policies) first.  Finally, there are a few special [route options](http://beta.sailsjs.org/#/documentation/concepts/Routes/RouteTargetSyntax.html?q=route-target-options) which allow a route to be "skipped" for certain kinds of requests.
+ The router can also programmatically **bind** a **route** to any valid route target, including canonical Node middleware functions (i.e. `function (req, res, next) {}`).  However, you should always use the conventional [route target syntax](http://beta.sailsjs.org/#/documentation/concepts/Routes/RouteTargetSyntax.html) when possible- it streamlines development, simplifies training, and makes your app more maintainable.



### Automatic Routes

In addition to your custom routes, Sails binds many routes for you automatically.  If a URL doesn't match a custom route, it may match one of the automatic routes and still generate a response.  The main types of automatic routes in Sails are:

* [Blueprint routes](http://beta.sailsjs.org/#/documentation/reference/blueprint-api?q=blueprint-routes), which provide your [controllers](http