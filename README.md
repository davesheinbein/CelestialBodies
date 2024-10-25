<<<<<<< HEAD
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
=======
Complete list of terminal commands with comments explaining each step:

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
(11, 6, 11, 'planet11', 500, 750, 1500.75, 'solid', true, true),
(12, 6, 12, 'planet12', 500, 750, 1500.75, 'solid', true, true);

-- Insert data into the 'moon' table
INSERT INTO moon VALUES 
(1,   1, 'moon1', 500, 750, 1500.75, 'solid', true, true),
(2,   2, 'moon2', 500, 750, 1500.75, 'solid', true, true),
(3,   3, 'moon3', 500, 750, 1500.75, 'solid', true, true),
(4,   4, 'moon4', 500, 750, 1500.75, 'solid', true, true),
(5,   5, 'moon5', 500, 750, 1500.75, 'solid', true, true),
(6,   6, 'moon6', 500, 750, 1500.75, 'solid', true, true),
(7,   7, 'moon7', 500, 750, 1500.75, 'solid', true, true),
(8,   8, 'moon8', 500, 750, 1500.75, 'solid', true, true),
(9,   9, 'moon9', 500, 750, 1500.75, 'solid', true, true),
(10, 10, 'moon10', 500, 750, 1500.75, 'solid', true, true),
(11, 11, 'moon11', 500, 750, 1500.75, 'solid', true, true),
(12, 11, 'moon12', 500, 750, 1500.75, 'solid', true, true),
(13, 11, 'moon13', 

500, 750, 1500.75, 'solid', true, true),
(14, 11, 'moon14', 500, 750, 1500.75, 'solid', true, true),
(15, 11, 'moon15', 500, 750, 1500.75, 'solid', true, true),
(16, 11, 'moon16', 500, 750, 1500.75, 'solid', true, true),
(17, 11, 'moon17', 500, 750, 1500.75, 'solid', true, true),
(18, 11, 'moon18', 500, 750, 1500.75, 'solid', true, true),
(19, 11, 'moon19', 500, 750, 1500.75, 'solid', true, true),
(20, 11, 'moon20', 500, 750, 1500.75, 'solid', true, true);

-- Insert data into the 'more_info' table
INSERT INTO more_info VALUES
(1, 1, 'info1', 'lorem impsum'),
(2, 2, 'info2', 'lorem impsum'),
(3, 3, 'info3', 'lorem impsum'),
(4, 4, 'info4', 'lorem impsum'),
(5, 5, 'info5', 'lorem impsum');
```

### 5. **Verify Inserted Data**
```sql
-- Select all rows from 'galaxy' table
SELECT * FROM galaxy;

-- Select all rows from 'star' table
SELECT * FROM star;

-- Select all rows from 'planet' table
SELECT * FROM planet;

-- Select all rows from 'moon' table
SELECT * FROM moon;

-- Select all rows from 'more_info' table
SELECT * FROM more_info;
```

### 6. **Add Primary and Foreign Key Constraints**
```sql
-- Add primary keys
ALTER TABLE galaxy    ADD PRIMARY KEY (galaxy_id);
ALTER TABLE star      ADD PRIMARY KEY (star_id);
ALTER TABLE planet    ADD PRIMARY KEY (planet_id);
ALTER TABLE moon      ADD PRIMARY KEY (moon_id);
ALTER TABLE more_info ADD PRIMARY KEY (more_info_id);

-- Add foreign key constraints
ALTER TABLE galaxy ADD FOREIGN KEY (star_id)   REFERENCES star   (star_id);
ALTER TABLE star   ADD FOREIGN KEY (galaxy_id) REFERENCES galaxy (galaxy_id);
ALTER TABLE star   ADD FOREIGN KEY (planet_id) REFERENCES planet (planet_id);
ALTER TABLE planet ADD FOREIGN KEY (star_id)   REFERENCES star   (star_id);
ALTER TABLE planet ADD FOREIGN KEY (moon_id)   REFERENCES moon   (moon_id);
ALTER TABLE moon   ADD FOREIGN KEY (planet_id) REFERENCES planet (planet_id);
```

### 7. **Dump the Database into a SQL File**
```bash
# Export the 'universe' database structure and data to a file called universe.sql
pg_dump -cC --inserts -U freecodecamp universe > universe.sql
```

### 8. Flowchart

```
+---------------------------+
|      Start Process        |
+---------------------------+
             |
             v
+---------------------------+
| Connect to PostgreSQL     |
| psql --username=...      |
+---------------------------+
             |
             v
+---------------------------+
| Create Database 'universe'|
| CREATE DATABASE universe;  |
+---------------------------+
             |
             v
+---------------------------+
| Create Tables             |
| CREATE TABLE galaxy (...); |
| CREATE TABLE star (...);   |
| CREATE TABLE planet (...); |
| CREATE TABLE moon (...);   |
| CREATE TABLE more_info (...); |
+---------------------------+
             |
             v
+---------------------------+
| Verify Table Creation     |
| \dt                       |
+---------------------------+
             |
             v
+---------------------------+
| Insert Data               |
| INSERT INTO galaxy VALUES; |
| INSERT INTO star VALUES;   |
| INSERT INTO planet VALUES; |
| INSERT INTO moon VALUES;   |
| INSERT INTO more_info VALUES; |
+---------------------------+
             |
             v
+---------------------------+
| Verify Inserted Data      |
| SELECT * FROM galaxy;     |
| ...                       |
+---------------------------+
             |
             v
+---------------------------+
| Add Constraints           |
| ALTER TABLE ...           |
+---------------------------+
             |
             v
+---------------------------+
| Dump Database to SQL File |
| pg_dump -cC ...          |
+---------------------------+
             |
             v
+---------------------------+
|      End Process          |
+---------------------------+
```

### 9. Entity-Relationship Diagram (ERD)

The following diagram illustrates the relationships between the tables in the **universe** database, including galaxies, stars, planets, moons, and additional information.

```
+-------------------+
|      Galaxy       |
+-------------------+
| galaxy_id (PK)   |
| star_id (FK)     |
| name              |
| area              |
| volume            |
| age               |
| material          |
| has_life          |
| has_water         |
+-------------------+
         |
         | 1
         |
         | M
+-------------------+
|       Star        |
+-------------------+
| star_id (PK)     |
| galaxy_id (FK)   |
| planet_id (FK)   |
| name              |
| area              |
| volume            |
| age               |
| material          |
| has_life          |
| has_water         |
+-------------------+
         |
         | 1
         |
         | M
+-------------------+
|      Planet       |
+-------------------+
| planet_id (PK)   |
| star_id (FK)     |
| moon_id (FK)     |
| name              |
| area              |
| volume            |
| age               |
| material          |
| has_life          |
| has_water         |
+-------------------+
         |
         | 1
         |
         | M
+-------------------+
|       Moon        |
+-------------------+
| moon_id (PK)     |
| planet_id (FK)   |
| name              |
| area              |
| volume            |
| age               |
| material          |
| has_life          |
| has_water         |
+-------------------+

+-------------------+
|     More_Info     |
+-------------------+
| more_info_id (PK)|
| object_id         |
| name              |
| description       |
+-------------------+
```

### Explanation of ERD Components:
- **Galaxy**: Contains properties of a galaxy, including links to stars.
- **Star**: Holds star attributes, including links to galaxies and planets.
- **Planet**: Describes planets and links to stars and moons.
- **Moon**: Contains properties of moons linked to planets.
- **More_Info**: Provides additional details for various celestial objects, referencing their IDs.

>>>>>>> 4785d7d (update)
