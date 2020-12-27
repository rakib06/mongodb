```python
Microsoft Windows [Version 10.0.18363.1256]
(c) 2019 Microsoft Corporation. All rights reserved.

C:\Users\RakibulHasan>mongo
MongoDB shell version v4.4.2
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("75dad89b-e08e-4b30-8e04-3115129ddeff") }
MongoDB server version: 4.4.2
---
The server generated these startup warnings when booting:
        2020-12-27T13:38:18.143+06:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
---
---
        Enable MongoDB's free cloud-based monitoring service, which will then receive and display
        metrics about your deployment (disk utilization, CPU, operation statistics, etc).

        The monitoring data will be available on a MongoDB website with a unique URL accessible to you
        and anyone you share the URL with. MongoDB may use this information to make product
        improvements and to suggest MongoDB products and deployment options to you.

        To enable free monitoring, run the following command: db.enableFreeMonitoring()
        To permanently disable this reminder, run the following command: db.disableFreeMonitoring()
---
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
test    0.000GB
> use test
switched to db test
> db show collection
uncaught exception: SyntaxError: unexpected token: identifier :
@(shell):1:3
> db show collections
uncaught exception: SyntaxError: unexpected token: identifier :
@(shell):1:3
> show collections
products
> db.products.insert({"id": 1, "name": "Laptop"})
WriteResult({ "nInserted" : 1 })
> db.products.insert({"id": 2, "size": "Laptop"})
WriteResult({ "nInserted" : 1 })
> db.products.insert({"id": 2, "phone": ["1", "2"]})
WriteResult({ "nInserted" : 1 })
> db.products.insert({"id": 2, "phone": ["1", "2"]})
WriteResult({ "nInserted" : 1 })
> db.dropDatabase()
{ "dropped" : "test", "ok" : 1 }
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
> use acme
switched to db acme
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
> db
acme
> db.createCollections('post')
uncaught exception: TypeError: db.createCollections is not a function :
@(shell):1:1
> show collections()
uncaught exception: Error: don't know how to show [collections()] :
shellHelper.show@src/mongo/shell/utils.js:1191:11
shellHelper@src/mongo/shell/utils.js:819:15
@(shellhelp2):1:1
> db.createCollection('post')
{ "ok" : 1 }
> show collections
post
> show dbs
acme    0.000GB
admin   0.000GB
config  0.000GB
local   0.000GB
> db.posts.insert({
... title: 'Post One',
... body: 'Body of post one',
... tags: ['news', 'events'],
... user: {
... name: 'Rakibul Hasan',
... status: 'SE'
... }
... date: Date()
... })
uncaught exception: SyntaxError: missing } after property list :
@(shell):9:0
> db.posts.insert({
... title: 'Post One',
... body: 'Body of post one',
... tags: ['news', 'events'],
... user: {
...  name: 'Rakibul Hasan',
... status: 'SE'
...  }
... date: Date()})
uncaught exception: SyntaxError: missing } after property list :
@(shell):9:0
> db.posts.insert({
... title: 'Post One',
... body: 'Body of post one',
... tags: ['news', 'events'],
... user: {
...  name: 'Rakibul Hasan',
... status: 'SE'
...       },
... date: Date()})
WriteResult({ "nInserted" : 1 })
> db.posts.insert(
... {
... title: 'Post Two',
... body: 'Body of post one',
... category: 'Technology'
... date: Date()
... },
... {
... title: 'Post Three',
... body: 'Body of post 3',
... tags: ['news', 'events'],
... category: 'Technology'
... date: Date()
... },
... {
... title: 'Post 4',
... body: 'Body of post 4',
... category: 'Technology'
... date: Date()
... },
...
... )
uncaught exception: SyntaxError: missing } after property list :
@(shell):6:0
> db.posts.insert(
... {
... title: 'Post Two',
... body: 'Body of post one',
... category: 'Technology'
... date: Date()
... },
... {
... title: 'Post Three',
... body: 'Body of post 3',
... tags: ['news', 'events'],
... category: 'Technology'
... date: Date()
... },
... {
... title: 'Post 4',
... body: 'Body of post 4',
... category: 'Technology'
... date: Date()
... }
...
... )
uncaught exception: SyntaxError: missing } after property list :
@(shell):6:0
> db.posts.insert(
... {
... title: 'Post Two',
... body: 'Body of post one',
... category: 'Technology',
... date: Date()
... },
... {
... title: 'Post Three',
... body: 'Body of post 3',
... tags: ['news', 'events'],
... category: 'Technology'
... date: Date()
... },
... {
... title: 'Post 4',
... body: 'Body of post 4',
... category: 'Technology',
... date: Date()
... }
...
... )
uncaught exception: SyntaxError: missing } after property list :
@(shell):13:0
> db.posts.insert(
... {
... title: 'Post Two',
... body: 'Body of post one',
... category: 'Technology',
... date: Date()
... },
... {
... title: 'Post Three',
... body: 'Body of post 3',
... tags: ['news', 'events'],
... category: 'Technology',
... date: Date()
... },
... {
... title: 'Post 4',
... body: 'Body of post 4',
... category: 'Technology',
... date: Date()
... }
... )
WriteResult({ "nInserted" : 1 })
> db.posts.find()
{ "_id" : ObjectId("5fe865916adfb96ed8869091"), "title" : "Post One", "body" : "Body of post one", "tags" : [ "news", "events" ], "user" : { "name" : "Rakibul Hasan", "status" : "SE" }, "date" : "Sun Dec 27 2020 16:44:33 GMT+0600 (Bangladesh Standard Time)" }
{ "_id" : ObjectId("5fe867486adfb96ed8869092"), "title" : "Post Two", "body" : "Body of post one", "category" : "Technology", "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)" }
> db.posts.find().pretty()
{
        "_id" : ObjectId("5fe865916adfb96ed8869091"),
        "title" : "Post One",
        "body" : "Body of post one",
        "tags" : [
                "news",
                "events"
        ],
        "user" : {
                "name" : "Rakibul Hasan",
                "status" : "SE"
        },
        "date" : "Sun Dec 27 2020 16:44:33 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867486adfb96ed8869092"),
        "title" : "Post Two",
        "body" : "Body of post one",
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)"
}
> db.posts.insert(
...
... {
... title: 'Post Three',
... body: 'Body of post 3',
... tags: ['news', 'events'],
... category: 'Technology',
... date: Date()
... },
... {
... title: 'Post 4',
... body: 'Body of post 4',
... category: 'Technology',
... date: Date()
... }
... )
WriteResult({ "nInserted" : 1 })
> db.posts.find().pretty()
{
        "_id" : ObjectId("5fe865916adfb96ed8869091"),
        "title" : "Post One",
        "body" : "Body of post one",
        "tags" : [
                "news",
                "events"
        ],
        "user" : {
                "name" : "Rakibul Hasan",
                "status" : "SE"
        },
        "date" : "Sun Dec 27 2020 16:44:33 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867486adfb96ed8869092"),
        "title" : "Post Two",
        "body" : "Body of post one",
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867c86adfb96ed8869093"),
        "title" : "Post Three",
        "body" : "Body of post 3",
        "tags" : [
                "news",
                "events"
        ],
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:54:00 GMT+0600 (Bangladesh Standard Time)"
}
> db.posts.find({category: "news"})
> db.posts.find({category: "News"})
> db.posts.find({category: "Technology"})
{ "_id" : ObjectId("5fe867486adfb96ed8869092"), "title" : "Post Two", "body" : "Body of post one", "category" : "Technology", "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)" }
{ "_id" : ObjectId("5fe867c86adfb96ed8869093"), "title" : "Post Three", "body" : "Body of post 3", "tags" : [ "news", "events" ], "category" : "Technology", "date" : "Sun Dec 27 2020 16:54:00 GMT+0600 (Bangladesh Standard Time)" }
> db.posts.find({category: "Technology"}).pretty()
{
        "_id" : ObjectId("5fe867486adfb96ed8869092"),
        "title" : "Post Two",
        "body" : "Body of post one",
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867c86adfb96ed8869093"),
        "title" : "Post Three",
        "body" : "Body of post 3",
        "tags" : [
                "news",
                "events"
        ],
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:54:00 GMT+0600 (Bangladesh Standard Time)"
}
> db.posts.find()sort({title:1}).pretty()
uncaught exception: SyntaxError: unexpected token: identifier :
@(shell):1:15
> db.posts.find()sort({title: 1}).pretty()
uncaught exception: SyntaxError: unexpected token: identifier :
@(shell):1:15
> db.posts.find().sort({title: 1}).pretty()
{
        "_id" : ObjectId("5fe865916adfb96ed8869091"),
        "title" : "Post One",
        "body" : "Body of post one",
        "tags" : [
                "news",
                "events"
        ],
        "user" : {
                "name" : "Rakibul Hasan",
                "status" : "SE"
        },
        "date" : "Sun Dec 27 2020 16:44:33 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867c86adfb96ed8869093"),
        "title" : "Post Three",
        "body" : "Body of post 3",
        "tags" : [
                "news",
                "events"
        ],
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:54:00 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867486adfb96ed8869092"),
        "title" : "Post Two",
        "body" : "Body of post one",
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)"
}
> db.posts.find().sort({category: 1}).pretty()
{
        "_id" : ObjectId("5fe865916adfb96ed8869091"),
        "title" : "Post One",
        "body" : "Body of post one",
        "tags" : [
                "news",
                "events"
        ],
        "user" : {
                "name" : "Rakibul Hasan",
                "status" : "SE"
        },
        "date" : "Sun Dec 27 2020 16:44:33 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867486adfb96ed8869092"),
        "title" : "Post Two",
        "body" : "Body of post one",
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867c86adfb96ed8869093"),
        "title" : "Post Three",
        "body" : "Body of post 3",
        "tags" : [
                "news",
                "events"
        ],
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:54:00 GMT+0600 (Bangladesh Standard Time)"
}
> db.posts.find().sort({title: -1}).pretty()
{
        "_id" : ObjectId("5fe867486adfb96ed8869092"),
        "title" : "Post Two",
        "body" : "Body of post one",
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867c86adfb96ed8869093"),
        "title" : "Post Three",
        "body" : "Body of post 3",
        "tags" : [
                "news",
                "events"
        ],
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:54:00 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe865916adfb96ed8869091"),
        "title" : "Post One",
        "body" : "Body of post one",
        "tags" : [
                "news",
                "events"
        ],
        "user" : {
                "name" : "Rakibul Hasan",
                "status" : "SE"
        },
        "date" : "Sun Dec 27 2020 16:44:33 GMT+0600 (Bangladesh Standard Time)"
}
> db.posts.find().sort({title: -1}).pretty().count()
3
> db.posts.find().sort({title: -1}).pretty().limit(2)
{
        "_id" : ObjectId("5fe867486adfb96ed8869092"),
        "title" : "Post Two",
        "body" : "Body of post one",
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:51:52 GMT+0600 (Bangladesh Standard Time)"
}
{
        "_id" : ObjectId("5fe867c86adfb96ed8869093"),
        "title" : "Post Three",
        "body" : "Body of post 3",
        "tags" : [
                "news",
                "events"
        ],
        "category" : "Technology",
        "date" : "Sun Dec 27 2020 16:54:00 GMT+0600 (Bangladesh Standard Time)"
}
> db.posts.find().sort({title: -1}).pretty().forEach(doc){ print('Blog Post :' + doc.title)})
uncaught exception: SyntaxError: unexpected token: '{' :
@(shell):1:55
> db.posts.find().sort({title: -1}).pretty().forEach(function(doc){ print('Blog Post :' + doc.title)})
Blog Post :Post Two
Blog Post :Post Three
Blog Post :Post One

```
