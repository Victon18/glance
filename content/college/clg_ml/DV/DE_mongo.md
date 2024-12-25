- MongoDB is an open-source, document-oriented NoSQL database management system.
# Freatures
1. Flexible Schema Design
----
- MongoDB allows dynamic, schema-less data structures.
- Easily accommodate changing data equirements.
---
2. Scalability and Performance
---
- Horizontal scaling supports large datasets and high traffic.
- Optimized read and write operations for fast performance.
---
3. Document-Oriented Storage
---
- Data is stored in flexible, JSON-like BSON documents.
- Self-contained units with rich data types and nested arrays.
---
4. Dynamic Queries
---
- Rich query language with support for complex queries.
- Utilize indexes to speed up query execution.
---
5. Aggregation Framework
---
- Perform advanced data transformations and analysis.
- Process data using multiple pipeline stages.
---
6. Open Source and Community
---
- MongoDB is open-source with a vibrant community.
- Regular updates, improvements, and support.


SQl vs Mongo
----

|SQL|MongoDB(NOSQL)|
|-|-|
|SQL databases are relational databases.|NoSQL databases are non-relational databases.|
|They use structured tables to store data in rows and columns.|They provide flexibility in data storage, allowing varied data types and structures.|
|Suitable for applications with well-defined schemas and fixed data structures.|Ideal for applications with dynamic or evolving data models.|
|E-commerce Platform, HR Management etc|CMS, Social Media Platforms, Gaming etc|
|Examples: MySQL, PostgreSQL, Oracle.|Examples: MongoDB, Cassandra, Redis.|

# JSON Vs BSON
- In MongoDB, we write in JSON format but behind it is stored in BSON (Binary JSON) format.
- Features
---
- Binary JSON Format: BSON, Binary JSON, is used in MongoDB for data storage and transmission.
- Efficient Storage: Designed for efficient data storage and transmission in MongoDB.
- Diverse Data Types: Supports a wider range of data types, including Binary, Date, and Regular Expression.
- Compact & Fast: BSON's binary format is more compact, leading to smaller storage and faster processing.
- Native to MongoDB: MongoDB stores data in BSON format, ensuring seamless integration.
- Performance Boost: Faster serialization improves data access and manipulation speed.

# Managing Databases
```
show dbs;
use <database-name>;
db.dropDatabase();
show collections;
db.createCollection('<collection-name>’);
db.<collection-name>.drop();
```
# Insert Operation
```
db.<collection-name>.insertOne({
field1: value1,
field2: value2,
...
});

db.<collection-name>.insertMany([
{ field1: value1, field2: value2, ... },
{ field1: value1, field2: value2, ... },
// ...
]);
```
# use of quotes
1. Special Characters
    - If a field name contains special characters or spaces, or starts with a numeric digit, using quotes is necessary.

2. Reserved Words
    - If a field name is a reserved keyword in MongoDB, use quotes to distinguish it from the reserved keyword.

# ordered and unordered inserts
1. Ordered Inserts
    - Default behavior is ordered, where MongoDB stops on the first error.
```
db.<collection-name>.insertMany([ doc1, doc2, ... ]);
```
2. Unordered Inserts
    - When executing bulk write operations with unordered flag, MongoDB continues processing after encountering an error.
```
db.<collection-name>.insertMany([ doc1, doc2, ... ], { ordered: false });
```
# case sensitivity
- Collection names are case-sensitive.
- Field names within documents are also case-sensitive.
```
db.Product.insertOne({name:'Sharma',age:30});
db.product.insertOne({name:'Sharma',age:30});
```
# Read
- find()
```
db.collection_name.find({ key: value })
```
- findOne()
```
db.collection_name.findOne({ key: value })
```
# importing JSON
```
#new.txt
Name,Class,Rollno,Contacts
Neu,12,256,32XX32455
Kira,11,123,44XX3535
Mari,10,345,65XX1341
Dora,11,124,98XX7645
```
---
```
mongoimport jsonfile.json –d database_name –c collection_name
mongoimport products.json -d shop -c products
mongoimport products.json -d shop -c products --jsonArray
```
- `--jsonArray` accepts the import of data expressed with multiple MongoDB documents within a single JSON array.

# comparison operator
- `$eq,$ne,$gt,$gte,$lt,$lte,$in,$nin`
```
db.products.find({ 'price': { $eq: 699 } });
db.category.find({ price: { $in: [249, 129, 39] }});
```
# cursors
- These are used to efficiently retrieve large result sets from queries, providing control over the data retrieval process.
- MongoDB retrieves query results in batches using cursors.

- Cursors are a pointer to the result set on the server.
- Cursors are used to iterate through query results.

- Automatic Batching
    - MongoDB retrieves query results in batches, not all at once.
    - Default batch size is usually 101 documents.
    - This improves memory efficiency and network usage.
- `count(),limit(),skip(),sort()`
```
db.products.find({ price: { $gt: 250 } }).count();
db.products.find({ price: { $gt: 250 } }).limit(5);
db.products.find({ price: { $gt: 250 } }).limit(5).skip(2);
db.products.find({ price: { $gt: 1250 } }'.limit(3).sort({ price: 1 });
```
- skip() can be inefficient for large offsets.
- Using sort() on large result sets may impact performance.
- Be cautious when using limit() and skip() on large collections.
- Consider using indexing to optimize query performance.
# Logical operators
- `$and,$or,$not,$nor`
```
{ $and: [ { condition1 }, { condition2 }, ...]
{ field: { $not: { operator: value } } }
```
# Elements operator
- `$exists,$type,$size`
```
{field:{$exists:<boolean>}}
{field:{$type:"<bson-data-type>"}}
{field:{$size:<array-length>}}
```
---
```
db.users.insertMany([
    { name: "Alice", age: 28 },
    { name: "Bob", age: 32, address: { city: "Chicago" } },
    { name: "Carol", age: 25 }
])
db.users.find({ "address": { $exists: true } })
```
# Projection
- To include specific fields, use projection with a value of 1 for the fields you want.
- To exclude fields, use projection with a value of 0 for the fields you want to exclude.
- You cannot include and exclude fields simultaneously in the same query projection.
```
db.collection.find({}, { field1: 1, field2: 1 })
```
# embedded document
- Query documents inside embedded documents using dot notation.

```
db.collection.find({ “parent.child”: value })
```
---
```
db.users.insertOne({
    name: "John Doe",
    age: 30,
    address: {street: "123 Main St",city: "New York",zip: "10001"}
})
db.users.find({ "address.city": "New York" })
```
# $expr

# $all vs $elemMatch
- The `$all` operator selects the documents where the value of a field is an array that contains all the specified elements.
```
{ <field>: { $all: [ <value1> , <value2> ... ] } }
db.products.find({ tags: { $all: ["electronics", "sale"] } });
```
- The $elemMatch operator matches documents that contain an array field with at least one element that matches all the specified query criteria.
```
{ <field>: { $elemMatch: { <query1>, <query2>, ... } } }
db.students.find({ grades: { $elemMatch: { subject: "math", score: { $gte: 90 } } } });
```
# update
```
db.collectionName.updateOne(
    { filter },
    { $set: { existingField: newValue, newField: "new value", // ... }, }
);
db.users.updateOne( { name: "Alice" },{$set:{age: 30, location: "New York"}});
db.collectionName.updateMany(
    { filter },
    { $set: { existingField: newValue, // ...
);
```
---
Removing and renaming feild
```
db.collectionName.updateOne( { filter }, { $unset: { fieldName: 1 } });
db.users.updateOne( { name: "Alice" }, { $unset: { age: 1 } } );
db.collectionName.updateOne(
    { filter },
    { $rename: { oldFieldName: "newFieldName" } }
);
db.users.updateOne( { name: "Alice" }, { $rename: { age: "years" } } );
```
---
updating arrays and embedded document
```
db.collectionName.updateOne(
    { filter },
    { $push: { arrayField: "new element" } }
);
db.users.updateOne(
    { name: "Alice" },
    { $push: { hobbies: "painting" } }
);
db.collectionName.updateOne(
    { filter },
    { $pop: { arrayField: value } }
);
db.users.updateOne( { name: "Alice" }, { $pop: { hobbies: -1 } } );
db.collectionName.updateOne(
    { filter },
    { $set: { "arrayField.$.text":
);
```
# delete
```
db.collectionName.deleteOne({ filter });
db.sales.deleteMany({ price: 55 });
```
# indexes
- Indexes are specialized data structures that optimize data retrieval speed in MongoDB.
- Indexes store a fraction of data in a more searchable format.
- Indexes are separate from collections and multiple indexes can exist per collection.
- Benefits of Indexes
    1. Faster Querying: Indexes drastically accelerate data retrieval, particularly for large collections.
    2. Efficient Sorting: Indexes facilitate rapid sorting based on specific fields.
    3. Improved Aggregation: Aggregation operations become more efficient with optimized indexes.
    4. Indexing on Multiple Fields: Complex queries can be executed efficiently by utilizing multiple fields in indexes.
# explain()
- Use explain() method to understand query execution in detail.
- Use it to measure the time taken to execute a query.
```
db.products.find({ name: 'Air Fryer' }).explain();
db.products.find({ name: 'Air Fryer' }).explain("executionStats");
```
# Managing Indexes
```
db.products.createIndex({ field: 1 });
(1) for storing indexes in ascending order.
(-1) for storing indexes in descending order.
db.collection.getIndexes();
//_id is a default index.
db.collection.dropIndex({ field: 1 });
db.collection.dropIndex(“index_name”);
```
## Unique and Text Indexes
```
db.collection.createIndex({ field: 1 }, { unique: true });
db.collection.createIndex({ field: "text" });
db.collection.find({ $text: { $search: "keyword" } });
```
Searching using index is faster than $regex searching.
```
db.products.find({ field: { $regex: "air" } })
```
---
---
When not to use Indexes?
---
-  Indexes on Rarely Used Fields
    Indexing fields that are seldom used in queries can consume unnecessary space and resources.
- Balancing Act
    Indexing requires disk space and memory. Overindexing can lead to resource strain and impact overall performance.
- Indexing Small Collections
    In smaller collections, the cost of index maintenance might outweigh the benefits gained from querying.

