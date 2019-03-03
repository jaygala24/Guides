## MongoDB - No SQL Document Database

Records are stored as **documents** and use json like syntax.

#### Advantages

- Scaling
- Much Faster in most type of operations

#### Installations for Ubuntu

[MongoDB Installations](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/ "MongoDB Installations")

Show the list of databases

```
show dbs
```

Create a database

```
use <database_name>
```


Show the current database

```
db
```

Create User with Roles (gives the user the readWrite and dbAdmin roles)

```
db.createUser( { user: "accountUser", pwd: "password", roles: [ "readWrite", "dbAdmin" ] } )
```

Create a collection

```
db.createCollection('<collection_name>')
```

Show the list of collections in a database

```
show collections
```

Insert a document in collection <collection_name>

```
Single document
db.<collection_name>.insert({field1: val1, field2: val2, field3: [val3, val4], ...});

Multiple document
db.<collection_name>.insert([{field1: val1, field2: val2, ...}, {field1: val1, field2: val2, ...}, ...]);
```

Find a document in collection <collection_name>

```
db.<collection_name>.find();

db.<collection_name>.find({field1: val1});

for formatted output
db.<collection_name>.find().pretty();

db.<collection_name>.find({field1: val1}).pretty();

db.<collection_name>.find({'field.subfield': val}).pretty();
```

Sort the documents in collection <collection_name> according to a field

```
Ascending Order
db.<collection_name>.find().sort({field1: 1});

Descending Order
db.<collection_name>.find().sort({field1: -1});
```

Count the number of documents in collection <collection_name>

```
db.<collection_name>.find().count();

db.<collection_name>.find({field1: val1}).count();
```

Limiting the number of documents in collection <collection_name>

```
db.<collection_name>.find().limit(5);

db.<collection_name>.find({field1: val1}).limit(5);
```

OR Operator (matchs the multiple documents)

```
db.<collection_name>.find({$or: [{field1: val1},{field2: val2}]}).pretty();
```

Greater Than Equal Operator

```
db.<collection_name>.find({field1: {$gte: val}}).pretty();
```

Greater Than Operator

```
db.<collection_name>.find({field1: {$gt: val}}).pretty();
```

Less Than Equal Operator

```
db.<collection_name>.find({field1: {$lte: val}}).pretty();
```

Less Than Operator

```
db.<collection_name>.find({field1: {$lt: val}}).pretty();
```

Update a document in collection <collection_name>

```
db.<collection_name>.update({field1: val1, ...}, {field1: val1, field2: val2, field3: val3, ...});
```

`Note: Here we need to specify all the previous fields that we want after the modifications along with the new fields otherwise it assigns only the new fields if not specified the previous fields. To overcome the above, we use set operator which will update that field without specifying all the other fields.`

Set Operator

```
db.<collection_name>.update({field1: val1, ...}, {$set: {field2, val2, field3: val3, ...}});
```

Increment Operator

```
db.<collection_name>.update({field1: val1, ...}, {$inc: {field2, val2, field3: val3}});
```

Unset Operator

```
db.<collection_name>.update({field1: val1, ...}, {$unset: {field2, val2});
```

Upsert Parameter (checks for the document and if not present then creates a new document)

```
db.<collection_name>.update({field1: val1, ...}, {field1: val1, field2: val2, field3: val3, ...}, {upsert: true});
```

Rename Operator

```
db.<collection_name>.update({field1: val1, ...}, {$rename: {'<old_field>': '<new_field>'});
```

Remove a document in collection <collection_name>

```
All the documents with the field field1 equal to val1
db.<collection_name>.remove({field1: val1});

Single document with the field field1 equal to val1
db.<collection_name>.remove({field1: val1}, {justOne: true});
```

Drop a database

```
use <database_name>
db.dropDatabase();
```
