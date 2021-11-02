MongoDB Command Line Examples
===

This command shows all databases

```
show dbs
```

This command creates and activates the database for editing. If it is already created, it only activates for editing.

```
use wikiDB
```

This command creates a collection.

```
db.createCollection("articles")
```

In order to see all the collections under a specific database, use these 2 commands,

```
use wikiDB
show collections
```

If you have a collection named "articles", in order to insert set of objects, use the following command. In this example we only entered a single object.

```
db.articles.insertMany(
    [
        {
            title: "REST",
            content: "REST is short for REpresentational State Transfer. It is an architectural style for designing APIs."
        }
    ]
)
```

Alternatively, only one single object can be inserted into a collection like so,

```
db.articles.insertOne(
    {
        title: "REST",
        content: "REST is short for REpresentational State Transfer. It is an architectural style for designing APIs."
    }
)
```

updateOne only updates the data in the first object it finds, whereas updateMany updates the data in all objects that matches the criteria. Remember that you cannot update the "_id" of an object as "_id" is an immutable value.

```
db.articles.updateOne(
    {_id: ObjectId("617dfc7b8d9356506c768e0c")},
    {
        $set: {title: "Hi!", content: "How are you?"}
    }
)
```

Next command only removes the content of the collection.

```
db.articles.remove({})
```

This command completely deletes the collection.

```
db.articles.drop()
```

This is an example of inserting many object into an already existing collection.

```
db.articles.insertMany(
    [
        {
            "_id" : ObjectId("5c139771d79ac8eac11e754a"),
            "title" : "API",
            "content" : "API stands for Application Programming Interface. It is a set of subroutine definitions, communication protocols, and tools for building software. In general terms, it is a set of clearly defined methods of communication among various components. A good API makes it easier to develop a computer program by providing all the building blocks, which are then put together by the programmer."
        },

        {
            "_id" : ObjectId("5c1398aad79ac8eac11e7561"),
            "title" : "Bootstrap",
            "content" : "This is a framework developed by Twitter that contains pre-made front-end templates for web design"
        },

        {
            "_id" : ObjectId("5c1398ecd79ac8eac11e7567"),
            "title" : "DOM",
            "content" : "The Document Object Model is like an API for interacting with our HTML"
        }
    ]
)
```

Once you enter an info, in order to find it, use the following command.

```
db.articles.find()
```

Alternatively, you can create filtering for finding things in collection.

```
db.articles.find(
    {"title": "DOM"}
)
```

For example if the result seems unreadable, you can use pretty() method.

```
db.articles.find().pretty()
```