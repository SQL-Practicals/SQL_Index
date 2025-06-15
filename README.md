                                                                # Tutorial - 04
# SQL Index

This project demonstrates how to:
- Create a `customers` table and insert data
- Create single and composite indexes
- View and drop indexes
- Handle unique index constraints

```sql
-- Step 1: Create Database and Switch to It
CREATE DATABASE customer;
USE customer;

-- Step 2: Create Table and Insert Data
-- This table holds customer records including name, age, address, and salary.
CREATE TABLE customers(
    ID INT NOT NULL,
    NAME VARCHAR(15) NOT NULL,
    AGE INT NOT NULL,
    ADDRESS VARCHAR(25),
    SALARY DECIMAL(10,4),
    PRIMARY KEY(ID)
);

-- Insert 20 customer records into the table.
INSERT INTO customers VALUES
(1, 'Ramesh', 32, 'Ahmedabad', 2000),
(2, 'Khilan', 25, 'Delhi', 1500),
(3, 'Kaushik', 23, 'Kota', 2000),
(4, 'Chaitali', 25, 'Mumbai', 6500),
(5, 'Hardik', 27, 'Bhopal', 8500),
(6, 'Komal', 22, 'Hyderabad', 4500),
(7, 'Muffy', 24, 'Pune', 10000),
(8, 'Raj', 26, 'Ahmedabad', 3000),
(9, 'Suman', 29, 'Chennai', 4000),
(10, 'Anil', 30, 'Delhi', 7200),
(11, 'Ravi', 28, 'Kolkata', 5100),
(12, 'Neha', 26, 'Bangalore', 6000),
(13, 'Aarti', 24, 'Lucknow', 3900),
(14, 'Ishaan', 31, 'Noida', 5500),
(15, 'Priya', 27, 'Indore', 7100),
(16, 'Yash', 23, 'Patna', 3200),
(17, 'Nitin', 33, 'Jaipur', 4600),
(18, 'Sneha', 25, 'Delhi', 3300),
(19, 'Aman', 22, 'Surat', 2800),
(20, 'Alok', 35, 'Agra', 6200);

-- Step 3: Create Indexes

-- Create a single-column index on the NAME column to improve search performance
CREATE INDEX idx_name ON customers(NAME);

-- Create a composite index on NAME and AGE to optimize queries that filter on both
CREATE INDEX idx_name_age ON customers(NAME, AGE);

-- View all indexes currently defined on the customers table
SHOW INDEX FROM customers;

-- Step 4: Unique Index (with Error Handling)
-- Attempt to create a UNIQUE index on ADDRESS will fail because duplicate addresses exist
CREATE UNIQUE INDEX idx_address_unique ON customers(ADDRESS); -- Will cause ERROR 1062

-- Insert an additional row to show how a duplicate address works with non-unique columns
INSERT INTO customers VALUES (21, 'Test', 28, 'Delhi', 5000);

-- Step 5: Drop Indexes

-- Drop the single-column index on NAME
DROP INDEX idx_name ON customers;

-- Drop the composite index on NAME and AGE
DROP INDEX idx_name_age ON customers;

-- View remaining indexes to confirm which ones exist
SHOW INDEX FROM customers;
