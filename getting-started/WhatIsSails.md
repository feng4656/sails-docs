# 什么是 Sails？


Sails 当然是一个网站开发框架。但退一步，这意味著什么？有时候，当我们提到「网站」，我们指的是「前端网站」。我们认为像是网页标准、HTML 5 或 CSS 3 的概念，以及像是 Backbone、Angular 或 jQuery 的框架。Sails 不是「那种」网站开发框架。Sails 与 Angular 及 Backbone 运作良好，但你永远不会使用 Sails _取代_这些类别库。

另一方面，有时候当我们谈论「网站开发框架」，我们指的是「后端网站」。这唤起了像是 REST、HTTP 或 WebSockets 的概念，以及像是 Java、Ruby 或 Node.js 的技术。一个「后端网站」框架可以帮助你做到一些事情，如建立 API、提供 HTML 文档及同时处理成千上万的使用者。Sails 是「那种」网站框架。



## 约定优于配置

Sails 完成许多与其他 MVC 网站应用程序框架相同的目标，使用许多相同的方法学。这样做是有目的的。一致的方式使得参与其中的任何人开发应用程序更具可预测性且高效率的。

想像一下，开始一份新的工作，在一家公司建立 Sails 应用程序。如果任何在你团队中的人曾使用如 Zend、Laravel、CodeIgniter、Cake、Grails、Django、ASP.NET MVC 或 Rails，会觉得很熟悉 Sails。不仅如此，一般来说，他们还可以了解 Sails 工程，如何撰写他们在过去已反复实践的基本模式；无论他们的背景是 PHP、Ruby、Java、C# 或 Node.js。那么你的第二个应用程序或第三个？每当你建立新的 Sails 应用程序，你以一个健全、熟悉的样版开始，让你更有效率。在许多情况下，你甚至可以回收重复使用一些后端程序码。

> **历史**
>
> Sails 没有发明这个概念，它[已经存在多年](https://en.wikipedia.org/wiki/Convention_over_configuration)。即使在 Ruby on Rails 那句「约定优于配置」（或称 CoC）流行之前，JavaBeans 借用了常见于 90 年代末期到 21 世纪初期，传统的 Java 网站框架极其冗长的 XML 设置到许多核心规范中。简单来说就是用简单的约定（Convention）来取代繁杂的配置（Configuration），简化开发者的工作。


## Loose Coupling

> TODO: explain why pushing towards an open standard for programming apps is important.
>
> TODO: more specifically, give some background why small, loosely coupled modules are good.
>
> TODO: explain how Sails core is a set of standalone, loosely coupled components (link to MODULES.md).
>
> TODO: discuss how a Sails app is a set of standalone, loosely coupled components:
>  + how each model, or controller, etc. is a node module.
>  + how policies are designed to be general-purpose and shared between apps and/or developers.
>  + how Sails strives to make adapter development as easy as possible, even for non-database integrations.
>
> TODO: explain how Sails is designed for any part to be rip-outable, overridden, or extended (hooks, generators, adapters)
>
> TODO: Explain how Sails can be used without any boilerplate files, just like Express, to fit an imperative programming style, or plug in as part of your existing Node / Node+Express app.

> Links:
> + [Unix philosophy](http://blog.izs.me/post/48281998870/unix-philosophy-and-node-js)
> + [Node culture](https://blog.nodejitsu.com/the-nodejs-philosophy/)


## Pragmatism

> TODO: set the stage- the purpose of any practical web framework should be to solve real-world use cases.  Node, being built on JavaScript, is the most intensely pragmatic thing to hit the scene since the introduction of Java.  It [will replace Java](http://readwrite.com/2013/08/09/why-javascript-will-become-the-dominant-programming-language-of-the-enterprise) [in the enterprise](http://blog.appfog.com/node-js-is-taking-over-the-enterprise-whether-you-like-it-or-not/).

> TODO: explain where this fits into the Node.js ecosystem, and pay homage to the PHP community (pragmatism is the best thing PHP has going for it)

> TODO: provide some examples of choices we've made w/ 