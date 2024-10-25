# Celestial Bodies Database

In this project, I created a relational database to store
information about celestial bodies, including galaxies,
stars, planets, and moons. The database will be managed
using PostgreSQL, and you'll implement tables,
relationships, and queries to meet the user stories.

This project is part of the
[FreeCodeCamp Relational Database Certification](https://www.freecodecamp.org/learn/relational-database).
[Build a celestial bodies database project](https://www.freecodecamp.org/learn/relational-database/build-a-celestial-bodies-database-project/build-a-celestial-bodies-database).

## Table of Contents

1.  [Database Setup](#step-2-database-setup): Steps to set
    up the database.
2.  [Create Database and Connect](#1-create-database-and-connect-to-it):
    Set up and connect to the database.
3.  [Create Tables](#2-create-tables): Define tables for
    `appointments`, `customers`, and `services`.
4.  [Verify Table Creation](#3-verify-table-creation):
    Ensure tables were created successfully.
5.  [Insert Data](#4-insert-data): Add initial data to the
    tables.
6.  [Verify Inserted Data](#5-verify-inserted-data): Confirm
    that data was inserted correctly.
7.  [Add Primary and Foreign Key Constraints](#6-add-primary-and-foreign-key-constraints):
    Ensure data integrity with relationships.
8.  [Dump the Database into a SQL File](#7-dump-the-database-into-a-sql-file):
    Backup database with pg_dump.
9.  [Flowchart](#8-flowchart): Overview of setup and
    workflow.
10. [Entity-Relationship Diagram (ERD)](#9-entity-relationship-diagram-erd):
    Visualize table relationships.
11. [Update Appointments, Customers, and Services](#10-update-appointments-customers-and-services):
    Instructions for updating existing records.

### Database Setup

### 1. **Create Database and Connect to It**

```bash
# Connect to PostgreSQL with the 'freecodecamp' username, using the 'postgres' database
psql --username=freecodecamp --dbname=postgres

# Create a new database named 'universe'
CREATE DATABASE universe;

# Connect to the newly created 'universe' database
\c universe
```

### 2. **Create Tables**

```sql
-- Create 'galaxy' table with various properties for a galaxy
CREATE TABLE galaxy (
    galaxy_id SERIAL NOT NULL,        -- Primary key (automatically incremented)
    star_id INTEGER NOT NULL,         -- Foreign key to 'star' table
    name VARCHAR(20) UNIQUE NOT NULL, -- Name of the galaxy (must be unique)
    area INTEGER,                     -- Area of the galaxy
    volume INTEGER,                   -- Volume of the galaxy
    age NUMERIC,                      -- Age of the galaxy
    material TEXT,                    -- Main material of the galaxy
    has_life BOOLEAN,                 -- Whether the galaxy supports life
    has_water BOOLEAN                 -- Whether the galaxy contains water
);

-- Create 'star' table with various properties for a star
CREATE TABLE star (
    star_id SERIAL NOT NULL,          -- Primary key (automatically incremented)
    galaxy_id INTEGER NOT NULL,       -- Foreign key to 'galaxy' table
    planet_id INTEGER NOT NULL,       -- Foreign key to 'planet' table
    name VARCHAR(20) UNIQUE NOT NULL, -- Name of the star (must be unique)
    area INTEGER,                     -- Area of the star
    volume INTEGER,                   -- Volume of the star
    age NUMERIC,                      -- Age of the star
    material TEXT,                    -- Main material of the star
    has_life BOOLEAN,                 -- Whether the star supports life
    has_water BOOLEAN                 -- Whether the star contains water
);

-- Create 'planet' table with various properties for a planet
CREATE TABLE planet (
    planet_id SERIAL NOT NULL,        -- Primary key (automatically incremented)
    star_id INTEGER NOT NULL,         -- Foreign key to 'star' table
    moon_id INTEGER NOT NULL,         -- Foreign key to 'moon' table
    name VARCHAR(20) UNIQUE NOT NULL, -- Name of the planet (must be unique)
    area INTEGER,                     -- Area of the planet
    volume INTEGER,                   -- Volume of the planet
    age NUMERIC,                      -- Age of the planet
    material TEXT,                    -- Main material of the planet
    has_life BOOLEAN,                 -- Whether the planet supports life
    has_water BOOLEAN                 -- Whether the planet contains water
);

-- Create 'moon' table with various properties for a moon
CREATE TABLE moon (
    moon_id SERIAL NOT NULL,          -- Primary key (automatically incremented)
    planet_id INTEGER NOT NULL,       -- Foreign key to 'planet' table
    name VARCHAR(20) UNIQUE NOT NULL, -- Name of the moon (must be unique)
    area INTEGER,                     -- Area of the moon
    volume INTEGER,                   -- Volume of the moon
    age NUMERIC,                      -- Age of the moon
    material TEXT,                    -- Main material of the moon
    has_life BOOLEAN,                 -- Whether the moon supports life
    has_water BOOLEAN                 -- Whether the moon contains water
);

-- Create 'more_info' table for additional details about objects
CREATE TABLE more_info (
    more_info_id SERIAL NOT NULL,     -- Primary key (automatically incremented)
    object_id INTEGER,                -- Object ID (could reference galaxy, star, etc.)
    name VARCHAR(20) UNIQUE NOT NULL, -- Unique name for the info
    description TEXT                  -- Description of the object
);
```

### 3. **Verify Table Creation**

```sql
-- Show a list of all tables in the current database (universe)
\dt
```

### 4. **Insert Data**

```sql
-- Insert data into the 'galaxy' table
INSERT INTO galaxy VALUES
(1, 1, 'galaxy1', 500, 750, 1500.75, 'solid', true, true),
(2, 2, 'galaxy2', 500, 750, 1500.75, 'solid', true, true),
(3, 3, 'galaxy3', 500, 750, 1500.75, 'solid', true, true),
(4, 4, 'galaxy4', 500, 750, 1500.75, 'solid', true, true),
(5, 5, 'galaxy5', 500, 750, 1500.75, 'solid', true, true),
(6, 6, 'galaxy6', 500, 750, 1500.75, 'solid', true, true);

-- Insert data into the 'star' table
INSERT INTO star VALUES
(1, 1, 1, 'star1', 500, 750, 1500.75, 'solid', true, true),
(2, 2, 2, 'star2', 500, 750, 1500.75, 'solid', true, true),
(3, 3, 3, 'star3', 500, 750, 1500.75, 'solid', true, true),
(4, 4, 4, 'star4', 500, 750, 1500.75, 'solid', true, true),
(5, 5, 5, 'star5', 500, 750, 1500.75, 'solid', true, true),
(6, 6, 6, 'star6', 500, 750, 1500.75, 'solid', true, true);

-- Insert data into the 'planet' table
INSERT INTO planet VALUES
(1,  1,  1, 'planet1', 500, 750, 1500.75, 'solid', true, true),
(2,  2,  2, 'planet2', 500, 750, 1500.75, 'solid', true, true),
(3,  3,  3, 'planet3', 500, 750, 1500.75, 'solid', true, true),
(4,  4,  4, 'planet4', 500, 750, 1500.75, 'solid', true, true),
(5,  5,  5, 'planet5', 500, 750, 1500.75, 'solid', true, true),
(6,  6,  6, 'planet6', 500, 750, 1500.75, 'solid', true, true),
(7,  6,  7, 'planet7', 500, 750, 1500.75, 'solid', true, true),
(8,  6,  8, 'planet8', 500, 750, 1500.75, 'solid', true, true),
(9,  6,  9, 'planet9', 500, 750, 1500.75, 'solid', true, true),
(10, 6, 10, 'planet10', 500, 750, 1500.75, 'solid', true, true),
(11, 6

, 11, 'planet11', 500, 750, 1500.75, 'solid', true, true),
(12, 6, 12, 'planet12', 500, 750, 1500.75, 'solid', true, true);

-- Insert data into the 'moon' table
INSERT INTO moon VALUES
(1, 1, 'moon1', 500, 750, 1500.75, 'solid', true, true),
(2, 2, 'moon2', 500, 750, 1500.75, 'solid', true, true),
(3, 3, 'moon3', 500, 750, 1500.75, 'solid', true, true),
(4, 4, 'moon4', 500, 750, 1500.75, 'solid', true, true),
(5, 5, 'moon5', 500, 750, 1500.75, 'solid', true, true),
(6, 6, 'moon6', 500, 750, 1500.75, 'solid', true, true);

-- Insert data into the 'more_info' table
INSERT INTO more_info VALUES
(1, 1, 'star_name1', 'some description'),
(2, 2, 'star_name2', 'some description'),
(3, 3, 'star_name3', 'some description');
```

### 5. **Verify Inserted Data**

```sql
-- Verify the data in the 'galaxy' table
SELECT * FROM galaxy;

-- Verify the data in the 'star' table
SELECT * FROM star;

-- Verify the data in the 'planet' table
SELECT * FROM planet;

-- Verify the data in the 'moon' table
SELECT * FROM moon;

-- Verify the data in the 'more_info' table
SELECT * FROM more_info;
```

### 6. **Add Primary and Foreign Key Constraints**

- A primary key is a unique identifier for a record in a
  table.
  - It ensures that no two rows have the same value for the
    primary key column(s).
- A foreign key is a field (or collection of fields) in one
  table that uniquely identifies a row of another table or
  the same table.
  - It establishes a relationship between the two tables.

```sql
-- Add primary key to 'galaxy' table
ALTER TABLE galaxy ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);

-- Add foreign key to 'star' table referencing 'galaxy' table
ALTER TABLE star ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES galaxy (galaxy_id);

-- Add primary key to 'star' table
ALTER TABLE star ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);

-- Add foreign key to 'planet' table referencing 'star' table
ALTER TABLE planet ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES star (star_id);

-- Add primary key to 'planet' table
ALTER TABLE planet ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);

-- Add foreign key to 'moon' table referencing 'planet' table
ALTER TABLE moon ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES planet (planet_id);

-- Add primary key to 'moon' table
ALTER TABLE moon ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);

-- Add primary key to 'more_info' table
ALTER TABLE more_info ADD CONSTRAINT more_info_pkey PRIMARY KEY (more_info_id);
```

### 7. **Dump the Database into a SQL File**

```bash
pg_dump --username=freecodecamp --no-owner --file=universe_dump.sql universe
```

### 8. **Flowchart**

![Flowchart](./images/flowchart.png)

### 9. **Entity-Relationship Diagram (ERD)**

![ERD](./images/erd.png)

### 10. **Update Appointments, Customers, and Services**

To update existing records in the database, use the `UPDATE`
statement.

#### Example of Updating a Record

To update the name of a star, for instance, you could use:

```sql
UPDATE star
SET name = 'new_star_name'
WHERE star_id = 1;  -- Assuming the star_id is 1
```

#### Updating Customers

Similarly, to update a customer's information:

```sql
UPDATE customers
SET name = 'new_customer_name'
WHERE customer_id = 1;  -- Assuming the customer_id is 1
```

#### Updating Services

To update a service's details:

```sql
UPDATE services
SET description = 'new_service_description'
WHERE service_id = 1;  -- Assuming the service_id is 1
```
