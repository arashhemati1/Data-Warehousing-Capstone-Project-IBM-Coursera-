# Module 1: OLTP Database Design

This module involves creating and setting up the OLTP database with MySQL as part of the Data Warehousing Capstone Project.

## Step 1: Create a Database
- **Task**: Create a new database named `sales`.
- **Code**:
  ```sql
  CREATE DATABASE sales;

## Step 2: Design a Table Named sales_data
- **Task**: Create the sales_data table in the sales database.
- **Code**:
  ```sql
  CREATE TABLE sales_data (
    product_id INT,
    customer_id INT,
    price INT,
    quantity INT,
    timestamp DATETIME
  );

## Step 3: Import Data from oltpdata.csv
- **Task**: Import data into the sales_data table from the oltpdata.csv file.
- **Code**:
  ```sql
    LOAD DATA INFILE '/path/to/oltpdata.csv'
    INTO TABLE sales_data
    FIELDS TERMINATED BY ',' 
    ENCLOSED BY '"'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS;

## Step 4: List the Tables in the Database
- **Task**: List all tables in the sales database to verify table creation.
- **Code**:
  ```sql
  SHOW TABLES;

## Step 5: Find the Count of Records in the sales_data Table
- **Task**: Task: Query the count of records in the sales_data table.
- **Code**:
  ```sql
  SELECT COUNT(*) AS record_count FROM sales_data;

## Step 6: Create an Index on the timestamp Field
- **Task**: Create an index named ts on the timestamp column to optimize queries.
- **Code**:
  ```sql
  CREATE INDEX ts ON sales_data (timestamp);

## Step 7: List Indexes on the sales_data Table
- **Task**: List all indexes on the sales_data table to verify the creation of the index.
- **Code**:
  ```sql
  SHOW INDEX FROM sales_data;

## Step 8: Write a Bash Script to Export Data
- **Task**: Write a bash script named datadump.sh to export all rows from the sales_data table to a file named sales_data.sql.
- Open your terminal in the Cloud IDE or your local machine.
- Create the script file by typing:
- **Code**:
  ```sh
  nano datadump.sh
  This will open a text editor where you can write your script.
-  Write the Bash Script:
- **Code**:
- ```sh
  #!/bin/bash

  # Define database and table names
  DATABASE="sales"
  TABLE="sales_data"
  OUTPUT_FILE="sales_data.sql"
  
  # Export data from the sales_data table to sales_data.sql
  mysqldump $DATABASE $TABLE > $OUTPUT_FILE
  
  # Print a success message
  echo "Data has been exported to $OUTPUT_FILE"
