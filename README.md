# Banking-Management-System
The Bank Management System is a SQL-based database project designed to manage customer accounts and financial transactions in a simplified banking environment. This project demonstrates the use of MySQL Database Concepts such as table creation, primary and foreign keys, constraints, joins, aggregate functions, stored procedures, and views.

# Purpose of the Project

The purpose of this project is to create a structured and efficient database system that can handle the essential operations of a banking environment. It aims to simplify the management of customer accounts and financial transactions by storing data securely, ensuring accuracy through constraints and triggers, and enabling easy retrieval of information using SQL queries.

This project serves as a practical demonstration of database concepts such as relational design, normalization, data integrity, automation, and reporting. It helps users, learners, and developers understand how real-world banking systems manage data behind the scenes while providing a strong foundation in SQL-based database development.

# Key Objectives

=> Customer Account Management

=> Secure Transaction Handling

=> Data Integrity and Consistency

=> Account Summary (View) and Query Support for Analysis

# Advantages

=> Efficient data management of accounts and transactions.

=> Accurate tracking of deposits and withdrawals. 

=> Maintains data integrity and security.

=> Supports reporting and financial analysis.

=> Scalable for more customers and transactions.

=> Helps in learning SQL concepts and database design.

# Disadvantage

=> Limited Interface that Works mainly via MySQL CLI or Workbench; no GUI for end-users.

=> Not designed for large-scale banking operations.

=> Lacks Security, advanced authentication and encryption features.

=> Requires manual script execution for some operations.

# Working Flow

=> Database Initialization

     Create the database (bank) and tables (Account and Transaction).
     Define constraints (primary keys, foreign keys, NOT NULL, ENUMs) to ensure data integrity.
     
=> Data Insertion

     Insert sample customer accounts into the Account table.
     Insert sample transactions (deposits and withdrawals) into the Transaction table.
     
=> Transaction Handling

     Users or bank staff add a new transaction.
     Each transaction is linked to a valid account via a foreign key.
     
=> Information Retrieval

     Users can run queries to view account details, transactions, and summaries.
     Stored procedures can generate mini statements (last 5 transactions).
     Views provide summarized account information (total deposits, withdrawals, balance).
     
=> Analysis and Reporting

     Execute aggregate queries to calculate totals, averages, or other analytics.
     Join queries combine account and transaction data for comprehensive reporting.
     
=> Maintenance and Updates

     Add new accounts or transactions as needed.
     Update account details if necessary (e.g., customer name or account type).
     Back up the database periodically to avoid data loss.
