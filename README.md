Name
----

mongodb-rest - REST server for MongoDB, forked from https://github.com/tdegrunt/mongodb-rest

Description
-----------

This is a REST server for MongoDB using Node, using the native node.js MongoDB driver.
The only reason this fork exists was to make a slightly customized instance that I 
could easily require/use at PaaS services.

Installation
------------

Installation is now via npm: `npm install panurgy-mongodb-rest`.

Try
---

After installation you can quickly try whether it works by issuing the following from the command line:
> curl -d '{ "A1" : 201 }' -H "Content-Type: application/json" http://localhost:3000/test/example1

This should add a document to the "test" db.example1 collection:
{
"A1": 201,
"_id": ObjectId("4e90e196b0c7f4687000000e")
}

Notes
-----

Supported REST requests:

* `GET /db/collection` - Returns all documents
* `GET /db/collection?query=%7B%22isDone%22%3A%20false%7D` - Returns all documents satisfying query
* `GET /db/collection?query=%7B%22isDone%22%3A%20false%7D&limit=2&skip=2` - Ability to add options to query (limit, skip, etc)
* `GET /db/collection/id` - Returns document with _id_
* `POST /db/collection` - Insert new document in collection (document in POST body)
* `PUT /db/collection/id` - Update document with _id_ (updated document in PUT body)
* `DELETE /db/collection/id` - Delete document with _id_

Flavors:

* Setup "sproutcore" as flavor, it will then change _id as returned by MongoDB into guid, as used by SproutCore, this allows for simpler DataSources.
* Setup "nounderscore" as flavor, it will then change _id into id.

Content Type:

* Please make sure `application/json` is used as Content-Type when using POST/PUT with request body's.

Dependencies:

* Are all indicated in package.json. So far I indicate the lowest version with which I tested the code. Sadly this can result in non-working code when later versions are used.

Testing
-------

Testing is now done using expresso. Just run the following in the main folder:
`expresso -s test/create.test.js test/delete.test.js test/update.test.js`
The SproutCore test needs to be run separately at the moment.

Future
------

Not much of a future planned here

Credits
-------
* [Tom de Grunt](https://github.com/tdegrunt/mongodb-rest)
* [MongoDB Driver](http://github.com/christkv/node-mongodb-native)
* [Express](http://expressjs.com/)
* [npm](http://npmjs.org/)
