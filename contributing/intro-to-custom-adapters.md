# Introduction to Custom Adapters for Sails / Waterline

> ##### Stability: Varies

## Reference
 
Please see the [adapter interface specification](https://github.com/balderdashy/sails-docs/blob/0.9/adapter-specification.md).



### What is an adapter?

 Adapters expose **interfaces**, which imply a conract to implemnt certain functionality.  This allows us to guarantee conventional usage patterns across multiple models, developers, apps, and even companies, making app code more maintainable, efficient, and reliable.  Adapters are useful for integrating with databases, open APIs, internal/proprietary web services, or even hardware.


### What kind of things can I do in an adapter?

Adapters are mainly focused on providing model-contextualized CRUD methods.  CRUD stands for create, read, update, and delete.  In Sails/Waterline, we call these methods `create()`, `find()`, `update()`, and `destroy()`.

For example, a `MySQLAdapter` implements a `create()` method which, internally, calls out to a MySQL database using the specified table name and connection informtion and runs an `INSERT ...` SQL query.

In practice, your adapter can really do anything it likes-- any method you write will be exposed on the raw connection objects and any models which use them.




## Why would I need a custom adapter?

When building a Sails app, the sending or receiving of any asynchronous communication with another piece of hardware can be normalized into an adapter.  (viz. API integrations) 

> **From Wikipedia:**
> *http://en.wikipedia.org/wiki/Create,_read,_update_and_delete*

> Although a relational database provides a common persistence layer in software applications, numerous other persistence layers exist. CRUD functionality can be implemented with an object database, an XML database, flat text files, custom file formats, tape, or card, for example.

In other words, Waterline is not just an ORM for your database.  It is a purpose-agnostic, open standard and toolset for integrating with all kinds of RESTful services, datasources, and devices, whether it's LDAP, Neo4J, or [a lamp](https://www.youtube.com/watch?v=OmcQZD_LIAE).
I know, I know... Not everything fits perfectly into a RESTful/CRUD mold!  Sometimes the service you're integrating with has more of an RPC-style interface, with one-off method names.  That's ok-- you can define any adapter methods you like! You still get all of the trickle-down config and connection-management goodness of Waterline core.



## Why should I build a custom adapter?

To recap, writing your API integrations as adapters is **easier**, takes **less time**, and **absorbs a considerable amount of risk**, since you get the advantage of a **standardized set of conventions**, a **documented API**, and a **built-in community** of other developers who have gone through the same process.  Best of all, you (and your team) can **reuse the adapter** in other projects, **speeding up development** and **saving time and money**.

Finally, if you choose to release your adapter as open-source, you provide a tremendous boon to our little framework and our budding Sails.js ecosystem.  Even if it's not via Sails, I encourage you to give back to the OSS community, even if you've never forked a repo before-- don't be intimidated, it's not that bad!

The more high-quality adapters we collectively release as open-source, the less repetitive work we all have to do when we integrate with various databases and services.  My vision is to make building server-side apps more fun and less repetitive for everyone, and that happens one community adapter at a time.

I tip my hat to you in advance :)




## What is an Adapter Interface?

The functionality of adapters is as varied as the services they connect.  That said, there is a standard library of methods, and a support matrix you should be aware of.  Adapters may implement some, all, or none of the interfaces below, but rest assured that **if an adapter implements one method in an interface, it should implement *all* of them**.  This is not always the case due to limitations and/or 