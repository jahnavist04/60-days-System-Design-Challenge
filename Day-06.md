# Databases 🗄️

## What is a Database?

A **database** is a system used to store, organize, and manage data.

Applications use databases to store information such as:

- User accounts
- Products
- Orders
- Messages
- Payments
- Posts

For example, when you create an account on a website, your information needs to be stored somewhere.

```text
User
  |
  | Request
  ↓
Application Server
  |
  | Store / Retrieve Data
  ↓
Database
```

---

## Why are Databases Needed?

Without a database, an application would have no reliable way to store and retrieve information.

A database allows us to:

- Store large amounts of data
- Retrieve data quickly
- Update existing data
- Delete data
- Keep data organized
- Manage multiple users accessing data

For example:

```text
User → Login
         |
         ↓
    Application
         |
         ↓
     Database
         |
         ↓
Check username & password
```

---

## Types of Databases

Databases are broadly divided into two categories:

- **SQL Databases**
- **NoSQL Databases**

---

## SQL Databases 🧮

SQL stands for **Structured Query Language**.

SQL databases store data in **tables** consisting of rows and columns.

For example, a Users table:

```text
+----+----------+-------------------+
| ID | Name     | Email             |
+----+----------+-------------------+
| 1  | John     | john@email.com    |
| 2  | Alice    | alice@email.com   |
| 3  | Bob      | bob@email.com     |
+----+----------+-------------------+
```

Some popular SQL databases are:

- MySQL
- PostgreSQL
- Oracle
- Microsoft SQL Server

---

## NoSQL Databases 📦

**NoSQL** databases are designed to store data in formats other than traditional tables.

They can store data as:

- Documents
- Key-value pairs
- Graphs
- Wide-column data

For example, a document database might store a user like this:

```text
{
    "id": 1,
    "name": "John",
    "email": "john@email.com"
}
```

Some popular NoSQL databases are:

- MongoDB
- Redis
- Cassandra
- DynamoDB

---

## SQL vs NoSQL

| SQL | NoSQL |
|---|---|
| Uses tables | Uses different data models |
| Structured data | Flexible data structure |
| Usually uses fixed schemas | Usually more flexible schemas |
| Strong relationships | Often designed for large-scale distributed data |
| Good for complex queries | Good for flexible and high-scale use cases |

Neither is always better.

The choice depends on the **requirements of the system**.

---

## What is a Database Query?

A **query** is a request made to a database to retrieve or modify data.

For example:

```sql
SELECT * FROM Users;
```

This asks the database to return all users.

We can also retrieve a specific user:

```sql
SELECT * FROM Users
WHERE id = 1;
```

The database then returns the matching data.

---

## Database in a Real-World System

Consider an online shopping application.

```text
                    ┌── Application Server
Users → Load Balancer
                    └── Application Server
                            |
                            ↓
                         Database
                            |
                    ┌───────┴───────┐
                    ↓               ↓
                 Products         Orders
```

The database can store information about products, users, orders, and payments.

As the application grows, the database can become one of the most important components to scale and optimize.

---

## Key Takeaways

- A database is used to store and manage application data.
- SQL databases organize data using tables.
- NoSQL databases provide more flexible data models.
- SQL and NoSQL are useful for different types of applications.
- Applications communicate with databases through queries.
- Database performance becomes increasingly important as a system grows.

## What I Learned Today

Today I learned that databases are one of the most important components of a system.

Choosing the right type of database depends on factors such as **data structure, scalability, performance, consistency, and application requirements**.

> **Good systems don't just store data — they store it in a way that can scale. 🗄️🚀**
