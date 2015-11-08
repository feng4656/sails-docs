# Adapter Interface Reference

> The adapter interface specification is currently under active development and may change.


## Semantic (interface)
> e.g. `RestAPI` or `MySQL`

> ##### Stability: [3](http://nodejs.org/api/documentation.html#documentation_stability_index) - Stable

Implementing the basic semantic interface (CRUD) is really a step towards a complete implementation of the Queryable interface, but with some services/datasources, about as far as you'll be able to get using native methods.

By supporting the Semantic interface, you also get the following:
+ if you write a `find()` function, developers can also use all of its synonyms, including dynamic finders and `findOne()`.  When they're called, they'll automatically be converted into the appropriate criteria object for the basic `find()` definition in your adapter.
+ as long as you implement basic `where` functionality (see `Queryable` below), Waterline can derive a simplistic version of associations support for you.  To optimize the default assumptions with native methods, override the appropriate methods in your adapter.

<!--

Deprecated-- should be moved to the pubsub hook docs:

+ When a socket subscribes to one or more "instance room(s)" (e.g. `Foo.subscribe(req, [3,2]`), it will receive `Foo.publishUpdate()` and `Foo.publishDestroy()` notifications for the relevant instances.
+ If a socket is subscribed to an "instance room", it will also be subscribed for "updates" and "destroys" to all instances of other models with a 1:* association with `Foo`.  The socket will also be notified of and subscribed to new matching instances of the associated model.

+ automatic socket.io pubsub support is provided by Sails-- it manages "rooms" for every class (collection) and each instance (model)
  + As soon as a socket subscribes to the "class room" using `Foo.subscribe()`, it starts receiving `Foo.publishCreate()` notifications any time they're fired for `Foo`.
-->
  

> All officially supported Sails.js database adapters implement the `Semantic` interface.

###### Class methods
+ `Model.create()`
+ `Model.find()`
+ `Model.update()`
+ `Model.destroy()`
+ Optimizations:
  + `findOrCreate()`
  + `createEach()`
  + Not yet available:
    + `destroyEach()`
    + `updateEach()`
    + `findOrCreateEach()`
    + `findAndUpdateOrCreate()`
    + `findAndUpdateOrCreateEach()`

<!--
+ `henry.destroy()`
-->


## Queryable (interface)

> ##### Stability: [3](http://nodejs.org/api/documentation.html#documentation_stability_index) - Stable

Query building features are common in traditional ORMs, but not at all a guarantee when working with Waterline.  Since Waterline adapters can support services as varied as Twitter, SMTP, and Skype, traditional assumptions around structured data don't always apply.

If query modifiers are enabled, the adapter must support `Model.find()`, as well as the **complete** query interface, or, where it is impossible to do so, at least provide helper notices.  If coverage of the interace is unfinished, it's still not a bad idea to make the adapter available, but it's important to clearly state the unifinished parts, and consequent limitations, up front.  This helps prevent the creation of off-topic issues in Sails/Waterline core, protects developers from unexpected consequences, and perhaps most importantly, helps focus contributors on high-value tasks.

> All officially supported Sails.js database adapters implement this interface.

###### Query modifiers
Query modifiers include filters:
+ `where`
+ `limit`
+ `skip`
+ `sort`
+ `select`
+ `distinct`

Boolean logic:
+ `and`
+ `or`
+ `not`

As well as `groupBy` and the aggregators:
+ `count`
+ `sum`
+ `min`
+ `max`
+ `average`

`IN` queries:
Adapters which implement `where` should recognize a list of values (e.g. `name: ['Gandalf', 'Merlin']`) as an `IN` query.  In other words, if `name` is either of those values, a match occured.  

Sub-attribute modifiers:
You are also responsible for sub-attribute modifiers, (e.g. `{ age: { '>=' : 65 } }`) with the notable exception of `contains`, `startsWith`, and 