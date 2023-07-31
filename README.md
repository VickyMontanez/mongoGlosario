# :sparkles:MongoDB:sparkles:

**MongoDB** is a modern database that can handle lots of data in a flexible and scalable way. It's different from traditional databases because it stores information in a format that looks like JSON (a data format commonly used in web development). This allows the data to be organized in a more natural and dynamic way.

Instead of using tables and rows like traditional databases, MongoDB uses "documents" that can have different structures and can hold more complex data, like lists and nested information. This makes it great for applications that deal with changing and diverse data.

In simple terms, MongoDB is like a super flexible storage system for large amounts of data that doesn't force you to fit your data into strict tables and rows. Instead, you can store data in a more free-flowing way, making it easier to work with modern and constantly evolving applications.



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