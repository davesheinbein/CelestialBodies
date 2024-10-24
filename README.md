# Celestial Bodies Database

This project is part of the
[FreeCodeCamp Relational Database Certification](https://www.freecodecamp.org/learn/relational-database/build-a-celestial-bodies-database-project/build-a-celestial-bodies-database).

## Project Overview

In this project, you will create a relational database to
store information about celestial bodies, including
galaxies, stars, planets, and moons. The database will be
managed using PostgreSQL, and you'll implement tables,
relationships, and queries to meet the user stories.

## Instructions

### Step 1: Complete the Project

1. Open the provided virtual machine environment.
2. Implement all the necessary user stories to pass the
   FreeCodeCamp tests.
3. Save a dump of your database in a `universe.sql` file.

### Step 2: Database Setup

#### 1. **Create the Database**

```bash
psql --username=freecodecamp --dbname=postgres
CREATE DATABASE universe;
\c universe
```

#### 2. **Create Tables**

You will create tables for galaxies, stars, planets, moons,
and more information.

```sql
CREATE TABLE galaxy (...);
CREATE TABLE star (...);
CREATE TABLE planet (...);
CREATE TABLE moon (...);
CREATE TABLE more_info (...);
```

#### 3. **Verify Table Creation**

Ensure your tables are created successfully.

```sql
\dt
```

#### 4. **Insert Sample Data**

Populate the database with sample records.

```sql
INSERT INTO galaxy VALUES (...);
INSERT INTO star VALUES (...);
INSERT INTO planet VALUES (...);
INSERT INTO moon VALUES (...);
INSERT INTO more_info VALUES (...);
```

#### 5. **Verify Data**

Use queries to check the inserted data.

```sql
SELECT * FROM galaxy;
SELECT * FROM star;
SELECT * FROM planet;
SELECT * FROM moon;
SELECT * FROM more_info;
```

#### 6. **Add Primary and Foreign Keys**

Add primary keys and establish relationships between tables.

```sql
ALTER TABLE galaxy ADD PRIMARY KEY (...);
ALTER TABLE star ADD FOREIGN KEY (...);
...
```

### Step 3: Export the Database

After completing the project, export the database into a SQL
file.

```bash
pg_dump -cC --inserts -U freecodecamp universe > universe.sql
```
