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



## :sparkles: Setting Up and Running a MongoDB Express Server :sparkles:

This guide explains how to set up and run a MongoDB Express server using the provided code files. You'll learn how to establish a connection to a MongoDB Atlas cluster and run the Express server to serve your application.

### :page_facing_up: Prerequisites

1. Node.js and npm installed on your machine.
2. A MongoDB Atlas account with a cluster set up.
3. Basic familiarity with MongoDB and Express.

### :rocket: Getting Started

1. **Create a New Project**

   Create a new project directory and navigate into it using your terminal.

   ```sh
   mkdir mongo-express-server
   cd mongo-express-server
   ```

2. **Install Dependencies**

   In your project folder, create a `package.json` file:

   ```sh
   npm init -y
   ```

   ```json
   Result:
   {
     "name": "mongo-express-server",
     "version": "1.0.0",
     "description": "",
     "main": "app.js",
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1"
     },
     "keywords": [],
     "author": "",
     "license": "ISC"
   }
   
   ```

   

   Install required dependencies:

   ```sh
   npm install express mongodb dotenv
   ```

   ```json
   Result: 
   {
     "name": "mongo-express-server",
     "version": "1.0.0",
     "description": "",
     "main": "app.js",
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1"
     },
     "keywords": [],
     "author": "",
     "license": "ISC",
     "devDependencies": {
       "dotenv": "16.3.1",
       "express": "4.18.2",
       "mongodb": "5.7.0"
     }
   }
   ```

   

   You need to config this file ``./package.json`` before the next step:

   ```json
   {
     "name": "mongo-express-server",
     "version": "1.0.0",
     "description": "",
     "main": "app.js",
     "type": "module",
     "scripts": {
        "dev": "nodemon --quiet app.js"
     },
     "keywords": [],
     "author": "",
     "license": "ISC",
     "devDependencies": {
       "dotenv": "16.3.1",
       "express": "4.18.2",
       "mongodb": "5.7.0"
     }
   }
   ```

   

3. **Create a MongoDB Atlas Cluster**

   Set up a MongoDB Atlas cluster and obtain the connection string. Make sure to note down the username, password, and database name used in the connection string.

   Here's a step-by-step breakdown of the process:

   1. **Sign Up or Log In:** If you don't already have an account, you'll need to sign up for MongoDB Atlas. Visit the MongoDB Atlas website (https://www.mongodb.com/cloud/atlas) and either sign up or log in with your existing account.

   2. **Create a New Project:** In MongoDB Atlas, projects are used to organize your clusters and resources. Create a new project by clicking the "New Project" button and following the prompts.

   3. **Build a Cluster:**

      - Click on the "Build a Cluster" button within your newly created project.
      - Choose a cloud provider and region for your cluster. MongoDB Atlas supports multiple cloud providers like AWS, Google Cloud, and Azure. Select the region that's geographically closest to your target audience for optimal performance.
      - Choose your desired cluster configuration, including the hardware specs and replication options. You can start with the free tier to get started.

   4. **Cluster Settings:**

      - Give your cluster a name that helps you identify it easily.
      - Adjust any additional settings as needed, such as enabling backup options, selecting the version of MongoDB, etc.

   5. **Database Access:**

      - Set up a database user who will have access to your cluster. This user's credentials will be used in the connection string to authenticate your application.
      - Choose a username and password for the user. Note down these credentials for later use.

   6. **Network Access:**

      - Configure your cluster to allow connections from your application. You can whitelist specific IP addresses or set up a more permissive rule to allow connections from anywhere (not recommended for production).

   7. **Review and Deploy:**

      - Review your cluster's configuration to ensure everything is set up correctly.
      - Click the "Create Cluster" button to initiate the cluster creation process. It may take a few minutes for the cluster to be fully provisioned.

      

4. **Obtain the Connection String:**

   After your MongoDB Atlas cluster is created, you'll need to obtain the connection string. The connection string is a URL-like string that your application uses to connect to the MongoDB cluster. It includes information about the username, password, cluster location, and other configuration details.

   1. **Locate the Connection String:**

      - In MongoDB Atlas, navigate to your cluster's dashboard.
      - Click the "Connect" button.

   2. **Choose a Connection Method:**

      - Choose "Connect Your Application" to get the connection string specifically for your application.

   3. **Copy the Connection String:**

      - You'll see a connection string that looks something like this:

        ```
        mongodb+srv://<username>:<password>@<cluster-url>/<database>
        ```

      - Replace `<username>`, `<password>`, `<cluster-url>`, and `<database>` with the appropriate values.
        
      

### :wrench: Configure Files

1. **Create `db/atlas.js`**

   Create a file named `atlas.js` inside the `db` folder in your project directory:

   ```javascript
   import dotenv from 'dotenv';
   import { MongoClient } from "mongodb";
   
   dotenv.config();
   
   export async function conx() {
       try {
           const uri = `mongodb+srv://${process.env.ATLAS_USER}:${process.env.ATLAS_PASSWORD}@atlascluster.3c0ouhb.mongodb.net/${process.env.ATLAS_DB}`;
           const options = {
               useNewUrlParser: true,
               useUnifiedTopology: true,
           };
           const client = await MongoClient.connect(uri, options);
           return client.db();
       } catch (error) {
           return { status: 500, message: error };
       }
   }
   ```

   

2. **Create `app.js`**

   Create a file named `app.js` in your project directory:

   ```javascript
   import dotenv from "dotenv";
   import express from "express";
   import { conx } from "./db/atlas.js";
   
   dotenv.config();
   const app = express();
   
   const config = JSON.parse(process.env.MY_SERVER);
   
   app.listen(config.port, () => {
       console.log(`Server is running at http://${config.hostname}:${config.port}`);
   });
   ```

   

3. **Create `.env` File**

   Create a `.env` file in your project directory and add the following:

   ```env
   ATLAS_USER=your_atlas_username
   ATLAS_PASSWORD=your_atlas_password
   ATLAS_DB=your_atlas_database_name
   MY_SERVER={"hostname": "localhost", "port": 3000}
   ```



### :rocket: Running the Server

1. **Start the Server**

   Run the following command to start your Express server:

   ```sh
   npm run dev
   ```

   Your server should be running at `http://localhost:3000` (or the port you've configured).

2. **Access the Server**

   Open your web browser and navigate to `http://localhost:3000` to see if your server is running successfully.

   

### :hammer_and_wrench: MongoDB Operations

The following code snippets demonstrate common MongoDB operations using the `mongodb` driver. Uncomment and integrate them into the `index.js` file:

1. **List All Collections:**

   ```javascript
   const collections = await db.listCollections().toArray();
   console.log("Collections:", collections);
   ```

2. **Check if a Collection Exists:**

   ```javascript
   const collectionExists = await db.listCollections({ name: "users" }).hasNext();
   console.log("Collection 'users' exists:", collectionExists);
   ```

3. **Create a Collection:**

   ```javascript
   const res = await db.createCollection("siMor");
   console.log("Collection created:", res);
   ```

4. **Insert One Document:**

   ```javascript
   const collection = db.collection("siMor");
   const insertResult = await collection.insertOne({
     name: "Vicky",
     surname: "Montañez",
     point: "jijijiji"
   });
   console.log("Inserted document:", insertResult.insertedId);
   ```

5. **Insert Many Documents:**

   ```javascript
   const collection = db.collection("siMor");
   const insertResult = await collection.insertMany([
     { a: 1 },
     { a: 2 },
     { a: 3 }
   ]);
   console.log("Inserted documents:", insertResult.insertedIds);
   ```

6. **Find All Documents in a Collection:**

   ```javascript
   const collection = db.collection("siMor");
   const findResult = await collection.find({}).toArray();
   console.log("Found documents:", findResult);
   ```

#### 

#### Autor✨

Vicky Vanessa Montañez Molina ---

- [vmontanez707@gmail.com](mailto:vmontanez707@gmail.com)
- https://github.com/VickyMontanezCampus