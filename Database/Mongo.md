# Mongo DB

- Document oriented , operational database
- Data is stores in form of collection. Each collection stores information on serveral records. Each record in the collection is stores as document.
- MongoDB allows developers to store rich JSON-like documents that map naturally to the objects they use in their code:

```
    {
    firstname: "Bob",
    lastname: "Smith",
    email: "bob@smith.com",
    address: {
        street: "100 Main St",
        city: "Anytown",
        state: "MO",
        zip: "11111"
    }
    }

```

### Commands

```
    # select or create a new database
    use <databasename>

    # create a collection
    db.createCollection('<collection name>'):

    # Insert into the collection
    db.Collection.insert():

    # find
    db.Collection.find():
```

### References

- [No SQL](https://www.mongodb.com/resources/basics/databases/nosql-explained)
- [SQL to MongoDB Mapping Chart](https://www.mongodb.com/docs/manual/reference/sql-comparison/)
