# :sparkles:MongoDB:sparkles:

**MongoDB** is a modern database that can handle lots of data in a flexible and scalable way. It's different from traditional databases because it stores information in a format that looks like JSON (a data format commonly used in web development). This allows the data to be organized in a more natural and dynamic way.

Instead of using tables and rows like traditional databases, MongoDB uses "documents" that can have different structures and can hold more complex data, like lists and nested information. This makes it great for applications that deal with changing and diverse data.

In simple terms, MongoDB is like a super flexible storage system for large amounts of data that doesn't force you to fit your data into strict tables and rows. Instead, you can store data in a more free-flowing way, making it easier to work with modern and constantly evolving applications.



<img src="https://raw.githubusercontent.com/VickyMontanezCampus/glosarioMongoDB/main/img/start.png" style="zoom: 200%;" />



## :sparkles:Key features of MongoDB:sparkles:



1. **Document-Oriented**: MongoDB stores data in documents that look like how data is usually organized in programming languages. This makes it easy to connect the data in your application to the data in the database.

2. **Scalability**: MongoDB can handle really big applications and can spread the data across many computers to keep things running fast and always available.

3. **Querying**: MongoDB can do advanced searches for data using a language that's easy to use and powerful. It can also make searching faster by creating special lists of data.

4. **No Schema Constraints**: In MongoDB, you don't have to decide on a fixed way to organize your data beforehand. You can change how things are structured without causing any problems.

5. **High Availability**: MongoDB automatically makes copies of your data so that if one computer fails, another can take over without losing anything.

6. **Aggregation Framework**: MongoDB has a toolset that can handle complex data tasks, like sorting, grouping, and analyzing information in a really smart way.

   

### :sparkles:How MongoDB works:sparkles:

1. <u>**Document Storage**</u>: MongoDB stores data in databases, which contain collections. Each collection is a set of documents that can have different fields and structures.
2. <u>**CRUD Operations**</u>: CRUD (Create, Read, Update, Delete) operations are used to interact with the database. Data can be inserted, retrieved, updated, and removed using the MongoDB query language.
3. <u>**Indexing**:</u> Indexes improve query performance by creating data structures that allow MongoDB to locate and access data more efficiently.
4. <u>**Sharding**:</u> When data grows beyond the capacity of a single server, MongoDB can distribute the data across multiple machines using sharding. Sharding is based on a shard key, and it ensures that related data is stored together.
5. <u>**Replication**</u>: MongoDB can create replicas of data across multiple servers to ensure high availability and data redundancy. These replicas can automatically take over if the primary node fails.



### :sparkles:Install MongoDB:sparkles:

To install MongoDB, follow these general steps:

1. **Choose your Operating System**: MongoDB supports various operating systems like Windows, macOS, and Linux. Make sure to download the appropriate installer for your OS.
2. **Download the Installer**: Go to the official MongoDB [website](https://www.mongodb.com/try/download/community) and download the latest version of MongoDB.
3. **Install MongoDB on Windows**:
   - Double-click the downloaded installer (msi file).
   - Follow the setup wizard instructions.
   - MongoDB will be installed in the default directory: `C:\Program Files\MongoDB\Server\<version>`. The installation should also add MongoDB to your system's PATH, allowing you to run MongoDB commands from the command prompt.
4. **Install MongoDB on Linux**:
   - For Linux, the installation steps vary depending on the package manager used by your distribution. Here are the general steps:
     - Import the MongoDB public GPG key.
     - Add the MongoDB repository to your package manager.
     - Install MongoDB using the package manager (e.g., apt, yum, dnf).
     - Start the MongoDB service.
     - Enable MongoDB to start on system boot (optional).
5. **Verify Installation**:
   - Open a terminal or command prompt.
   - Type `npm mongo --version` and press Enter. If MongoDB is installed correctly, this command displays the version of MongoDB you have installed on your system.



# :sparkles:Basic Methods of MongoDB✨

### use

In MongoDB, you don't need to explicitly create a  database. Simply choose a database when you start inserting data into  it. You can select or create a database using the `   use database_name` command.

```
use mi_base_de_datos;
```

​    

### createCollection

The `createCollection` function is used to  explicitly create a new collection in a database. While MongoDB allows  collections to be created dynamically when data is inserted, sometimes  it's useful to create a collection before inserting documents to have  greater control over its options, such as indexes, storage options,  validations, etc.

```
db.createCollection(name, options);
```

​    

### insertOne

The `insertOne` method is used to insert a single document into a collection.

```
db.my_collection_name.insertOne(document);

db.my_collection_name.insertOne({
  key1: "value1",
  key2: "value2"
});
```

​    

### insertMany

The `insertMany` method is used to insert multiple documents into a collection.

```
db.my_collection_name.insertMany([document1, document2, ...]);

db.my_collection_name.insertMany([
  { key1: "value1", key2: "value2" },
  { key1: "value3", key2: "value4" }
]);
```

​    

### updateOne and updateMany

The `update` method is used to update documents in a collection. However, starting from MongoDB 4.2, it's recommended to use `updateOne` or `updateMany` as the `update` method is deprecated.

```
//updateOne

db.my_collection_name.updateOne(
  { key1: "value1" },
  { $set: { key2: "new_value" } }
);

// updateMany

db.my_collection_name.updateMany(
  { key1: "value1" },
  { $set: { key2: "new_value" } }
);
```

​    

### deleteOne and deleteMany

Similar to `update`, the `delete` method is also deprecated, and it's recommended to use `deleteOne` or `deleteMany` to remove documents.

```
// deleteOne

db.my_collection_name.deleteOne({ key1: "value1" });

// deleteMany

db.my_collection_name.deleteMany({ key1: "value1" });
```

​    

### find

The `find` method is used to perform queries on a collection and retrieve documents that match a given filter.

```
db.my_collection_name.find(  filter );
```

​    

### aggregate

The `aggregate` method is used to perform  aggregation operations on the documents within a collection. This  enables more complex transformations and calculations to be performed on the data.

```
db.my_collection_name.aggregate([ { stage1 },  { stage2 }, ... ]);
```



​    

## :sparkles:MongoDB Operators:sparkles:



## $lookup

The `$lookup` operator is used to perform a  "left outer join" operation between two collections. It allows combining documents from one collection with documents from another collection  based on a common field.

```
db.my_collection_name.aggregate([
  {
    $lookup: {
      from: <collection to join>,
      localField: <field from the input documents>,
      foreignField:<field from the documents of the "from" collection>,
      as: <output array field>
    }
  }
]);
```

​    

## $project

The `$project` operator is used to select specific fields from documents and reshape the output.

```
db.my_collection_name.aggregate([
  {
    $project: {
      name: 1,
      price: 0
    }
  }
]);
```

​    

## $group

The `$group` operator is used to group documents and perform aggregation calculations within those groups.

```
db.my_collection_name.aggregate([
  {
    $group: {
      _id: <expression>, // Group key
      <field1>: { <accumulator1> : <expression1> },
      ...
    }
  }
]);
```

​    

## $match

The `$match` operator is used to filter documents in the aggregation pipeline stage.

```
db.my_collection_name.aggregate([
  {
    $match: <query>
  }
]);
```

​    

## $unwind

The `$unwind` operator is used to unwind an  array field into individual documents. This is useful when you want to  perform aggregation operations on individual elements within the array.

```
db.my_collection_name.aggregate([
  {
    $unwind: <field path> 
  }
]);
```

​    

## $addFields

The `$addFields` operator is used to add calculated fields to the documents in the aggregation pipeline stage.

```
db.my_collection_name.aggregate([
	{
        $addFields: { <newField>: <expression>, ... }
    }
]);
```

​    

## $sort

Sorts all input documents and returns them to the pipeline in sorted order..

```
 { $sort: { <field1>: <sort order>, <field2>: <sort order> ... } }
```

​    

## $sum

Calculates and returns the collective sum of numeric values. [`$sum`](https://www.mongodb.com/docs/upcoming/reference/operator/aggregation/sum/#mongodb-group-grp.-sum) ignores non-numeric values.

```
	 { $sum: <expression> }
```

​    

## $gt

selects those documents where the value of the field is greater than (i.e. >) the specified value.

```
    { field: { $gt: value } }
```

​    

## $gte

selects the documents where the value of the field is greater than or equal to (i.e. >=) a specified value (e.g. value.).

```
    { field: { $gte: value } }
```

​    

## $lt

selects the documents where the value of the field is less than (i.e. <) the specified value.

```
    { field: { $lt: value } }
```

​    

## $lte

selects the documents where the value of the field is less than or equal to (i.e. <=) the specified value.

```
    { field: { $lte: value } 
```





#### Autor✨

Vicky Vanessa Montañez Molina ---

- [vmontanez707@gmail.com](mailto:vmontanez707@gmail.com)
- https://github.com/VickyMontanezCampus