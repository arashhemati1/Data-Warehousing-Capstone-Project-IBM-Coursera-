# SoftCart Data Warehouse Schema

This document provides an overview of the SoftCart data warehouse schema, which is designed using a star schema approach. The schema includes a fact table (`softcartFactSales`) and several dimension tables (`softcartDimDate`, `softcartDimCategory`, `softcartDimItem`, `softcartDimCountry`). This structure enables efficient data analysis and reporting on sales data.

## Database Setup

Use the database and create all necessary tables with the following SQL script:

```sql
-- Use the database
USE softcart;

-- Create Date Dimension Table
CREATE TABLE softcartDimDate (
    DateID INT PRIMARY KEY,
    Date DATE NOT NULL,
    Month INT NOT NULL,
    MonthName VARCHAR(20),
    Year INT,
    Day INT,
    Weekday VARCHAR(10)
);

-- Create Category Dimension Table
CREATE TABLE softcartDimCategory (
    CategoryID INT PRIMARY KEY,
    CategoryName VARCHAR(50)
);

-- Create Item Dimension Table
CREATE TABLE softcartDimItem (
    ItemID INT PRIMARY KEY,
    ItemName VARCHAR(100),
    Price DECIMAL(10, 2)
);

-- Create Country Dimension Table
CREATE TABLE softcartDimCountry (
    CountryID INT PRIMARY KEY,
    CountryName VARCHAR(50)
);

-- Create Fact Sales Table
CREATE TABLE softcartFactSales (
    OrderID INT PRIMARY KEY,
    DateID INT,
    CategoryID INT,
    ItemID INT,
    CountryID INT,
    SalesAmount DECIMAL(10, 2),
    FOREIGN KEY (DateID) REFERENCES softcartDimDate(DateID),
    FOREIGN KEY (CategoryID) REFERENCES softcartDimCategory(CategoryID),
    FOREIGN KEY (ItemID) REFERENCES softcartDimItem(ItemID),
    FOREIGN KEY (CountryID) REFERENCES softcartDimCountry(CountryID)
);
