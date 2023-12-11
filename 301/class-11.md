# Class-11 Reading Notes: MongoDB and Mongoose; noSQL vs. SQL

source: [nosql vs sql](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool), chat GPT

## What are five differences between SQL and NoSQL databases

1. **Data Model:**
    - **SQL (Relational Databases):** Table-based structure where data is organized into rows and columns.
    - **NoSQL (Non-relational Databases):** Document-based, key-value pairs, graph databases, or wide-column stores. Data can be represented as collections of key-value pairs, documents, graphs, or wide-column stores without adhering to a standard schema.
2. **Schema:**
    - **SQL:** Predefined schema; the structure of the database is explicitly defined.
    - **NoSQL:** Dynamic schema for unstructured data; the database can evolve without a predefined schema.
3. **Scalability:**
    - **SQL:** Vertically scalable; increased load is managed by increasing the hardware resources (CPU, RAM, SSD) on a single server.
    - **NoSQL:** Horizontally scalable; additional servers are added to the database infrastructure to handle increased traffic and load.
4. **Query Language:**
    - **SQL:** Uses structured query language (SQL) for defining and manipulating data; powerful for complex queries.
    - **NoSQL:** Queries are focused on collections of documents; sometimes referred to as UnQL (Unstructured Query Language), with syntax varying across databases.
5. **Use Cases:**
    - **SQL:** Suitable for complex query-intensive environments, heavy-duty transactional applications, and scenarios where ACID properties (Atomicity, Consistency, Isolation, Durability) are crucial.
    - **NoSQL:** Preferred for hierarchical data storage, large datasets (big data), and scenarios where horizontal scalability and flexibility in data representation are important. It may not be the best fit for complex queries or high transactional applications.

##  What kind of data is a good fit for an SQL database?

- SQL databases are well-suited for scenarios where structured, relational data and the assurance of ACID properties (Atomicity, Consistency, Isolation, Durability) are essential.
- SQL databases are a good fit for applications that require a structured, relational data model with a strong emphasis on data integrity, consistency, and the ability to perform complex queries and transactions. Examples of such applications include financial systems, customer relationship management (CRM) systems, and inventory management systems.

### Give a real world example

CRM system is a real-world example where an SQL database is a good fit due to its structured nature, support for complex queries, transactional capabilities, and emphasis on data integrity—characteristics that align with the needs of managing customer relationships and interactions in a business context.

## What kind of data is a good fit a NoSQL database?

- NoSQL databases are well-suited for scenarios where flexibility, scalability, and the ability to handle unstructured or semi-structured data are crucial.
- good fit for applications that deal with unstructured or semi-structured data, require horizontal scalability, and benefit from a flexible and dynamic data model.

### Give a real world example

Examples include content management systems, real-time big data analytics, and applications with rapidly evolving data structures.

## Which type of database is best for hierarchical data storage?

For hierarchical data storage, document-oriented NoSQL databases are often considered the best fit. These databases allow you to store data in a flexible, nested, and hierarchical structure, making them well-suited for scenarios where the data has a tree-like or nested structure. One of the key advantages is that the data can be stored in a format similar to the application's natural data model, which simplifies the development process.

**Example Document-Oriented NoSQL Database: MongoDB**

MongoDB is a popular document-oriented NoSQL database that excels in handling hierarchical data. Here's why MongoDB is a good fit:

1. **JSON-like Documents:**
    - MongoDB stores data in BSON (Binary JSON) format, which is a binary representation of JSON-like documents. This allows developers to represent hierarchical relationships naturally.
2. **Flexible Schema:**
    - MongoDB has a dynamic schema, meaning that documents in the same collection can have different fields, allowing for flexibility in representing hierarchical structures without the need for a predefined schema.
3. **Nested Documents and Arrays:**
    - Documents in MongoDB can contain nested documents and arrays, enabling the representation of complex hierarchical relationships. This is particularly useful when dealing with nested or tree-like data structures.
4. **Rich Query Language:**
    - MongoDB provides a powerful query language that allows you to perform queries on nested documents and arrays. This flexibility makes it easier to retrieve and manipulate hierarchical data.
5. **Scalability:**
    - MongoDB is designed to scale horizontally, making it suitable for applications dealing with growing volumes of hierarchical data. You can distribute data across multiple servers to handle increased load.

## Which type of database is best for scalability?

When it comes to scalability, NoSQL databases are often preferred due to their inherent design for distributed and horizontally scalable architectures. NoSQL databases can efficiently handle large amounts of data and growing workloads by adding more servers to the database infrastructure. The type of NoSQL database that is best for scalability depends on the specific requirements of your application. Here are a few categories of NoSQL databases known for their scalability:

1. **Key-Value Stores:**
    - **Example:** Redis, DynamoDB, Riak
    - **Scalability:** Key-value stores are highly scalable because they distribute data across multiple nodes. Each key-value pair is stored and retrieved using a unique key, allowing for simple and efficient horizontal scaling.
2. **Document Stores:**
    - **Example:** MongoDB, CouchDB
    - **Scalability:** Document stores provide scalability by distributing collections of documents across multiple nodes. They are suitable for applications with flexible schemas and evolving data structures.
3. **Column-Family Stores:**
    - **Example:** Apache Cassandra, HBase
    - **Scalability:** Column-family stores offer scalability by horizontally partitioning data based on columns rather than rows. This design allows them to handle large amounts of data and traffic.
4. **Graph Databases:**
    - **Example:** Neo4j, Amazon Neptune
    - **Scalability:** Graph databases can be scalable when designed for distributed environments. They are particularly useful for applications involving complex relationships and network structures.
5. **Wide-Column Stores:**
    - **Example:** Google Bigtable, Apache Cassandra
    - **Scalability:** Wide-column stores distribute data across multiple nodes and are optimized for read and write operations on large datasets. They provide efficient scalability for specific use cases.

## SQL vs. noSQL

[sql vs nosql](https://www.youtube.com/watch?v=ZS_kXvOeQ5Y) (Video), chatGPT

1. **What does SQL stand for?**
   - SQL stands for "Structured Query Language."

2. **What is a relational database?**
   - A relational database is a type of database that organizes data into tables with rows and columns, and establishes relationships between these tables.

3. **What type of structure does a relational database work with?**
   - Relational databases work with a tabular structure, organizing data into tables with rows (records) and columns (attributes).

4. **What is a ‘schema’?**
   - A schema in the context of a database refers to the structure that defines how the data is organized, including tables, fields, relationships, and constraints.

5. **What is a NoSQL database?**
   - A NoSQL (Not Only SQL) database is a type of database that provides a flexible and scalable approach to storing and retrieving data, often without requiring a fixed schema. NoSQL databases can handle various data models, including key-value pairs, documents, graphs, and wide-column stores.

6. **How does it work?**
   - NoSQL databases work by offering a more flexible data model, often allowing data to be stored in a format that doesn't require a predefined schema. They are designed to scale horizontally, distributing data across multiple nodes to handle large volumes of data and traffic.

7. **What is inside of a MongoDB database?**
   - Inside a MongoDB database, data is stored in BSON (Binary JSON) format. Collections contain documents, which are JSON-like objects with key-value pairs. Documents within a collection can have different structures, providing flexibility.

8. **Which is more flexible - SQL or MongoDB? and why.**
   - MongoDB is generally considered more flexible because it allows for dynamic schemas, meaning that documents in the same collection can have different fields. This flexibility is advantageous in scenarios where data structures may evolve or vary.

9. **What is the disadvantage of a NoSQL database?**
   - One disadvantage of NoSQL databases is that they may lack the mature ecosystem and standardized query language found in SQL databases. Some NoSQL databases might have limited support, tools, or expertise compared to well-established SQL databases. Additionally, NoSQL databases may not be the best choice for applications that require complex queries and transactions.
