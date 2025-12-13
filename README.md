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

  Create the database (Project) and tables (Account and Transaction).

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

# STEP 1: Create and use database
    create database project;
    use project;

# STEP 2: Create Account table
    create table Account (Account_number int primary key , Customer_name varchar(30) not null, Gender enum ('male’, ‘female') not null, Account_type  enum('current’,’ savings') not null, Current_balance int not null);

# STEP 3: Insert sample data
    insert into account values(1001,'Virat','male','current',95000),(1002,'Rohit','male','current',88000),(1003,'Harmanpreet','female','current',65000),(1004,'Sachin','male','savings',105000),(1005,'Dhoni','male','savings',98000),(1006,'Smriti','female','current',101000),(1007,'Richa','female','savings',35000),(1008,'Dravid','male','savings',33000),(1009,'Bumrah','male','current',48000),(1010,'Hardik','male','current',91000),(1011,'Mithali','female','savings',23000), (1012,'Rahul','male','current',51000),(1013,'Harleen Deol','female','savings',21000),(1014,'Jemmiah','female','savings',85000),(1015,'Yuvraj','male','current',100000);

# STEP 4: Create Transaction table
    create table Transaction(Transaction_id int primary key, Account_number int not null, Transaction_type enum('withdraw','deposit') not null, Amount int not null, Transaction_date date not null);
# Add foreign key using alter command
    alter table transaction add constraint Account_number foreign key (Account_number) references Account (Account_number);

# STEP 5: Insert sample data
    insert into transaction values (101,1001,'withdraw',10000,now()),(102,1002,'withdraw',50000,now()),(103,1003,'withdraw',25000,now()),(104,1004,'deposit',12000,now()),(105,1005,'deposit',33000,now()),(106,1006,'withdraw',3000,now()),(107,1007,'withdraw',21000,now()),(108,1008,'deposit',50000,now()),(109,1009,'deposit',1000,now()),(110,1010,'withdraw',1200,now()),(111,1011,'deposit',5000,now()),(112,1012,'withdraw',17000,now()),(113,1013,'deposit',13000,now()),(114,1014,'withdraw',11000,now()),(115,1015,'deposit',31000,now());

# STEP 6: Queries and Output
# 1.	Retrieve all customer names who have a balance greater than 50,000.
    select customer_name from account where current_balance>50000;

# 2.Display account number, customer name, and account type of all customers having saving accounts.
    select account_number,customer_name,account_type from account where account_type='savings';

# 3.List all transactions made in the current month.
    select transaction_date ,transaction_type from transaction where now();

# 4. Show customers who have not made any transactions yet.
    select * from transaction where transaction_type is null;

# 5. Display the top 3 customers with the highest account balance.
    select customer_name, current_balance from account order by current_balance desc limit 3;

# 6. Retrieve all transactions where the amount is greater than 10,000.
    select * from transaction where amount>10000;

# 7. Show the total balance of all accounts combined.
    select sum(current_balance) from account;

# 8. List customers along with their total deposited amount.
    select sum(amount) as total_deposit_amount from transaction where transaction_type='deposit';

# 9. Find customers who made a withdrawal of more than 5,000.
    select customer_name, transaction_type, amount from account inner join transaction on account.account_number=transaction.account_number where transaction_type='withdraw' and amount>5000;

# 10. Display the most recent transaction date for each account
    select transaction_id ,transaction_date from transaction where now();

# 11. Retrieve the number of transactions each customer has made.
    select transaction_type from transaction where transaction_type is null;

# 12. List customers who have both SAVINGS and CURRENT accounts (if allowed).
    select customer_name, transaction_type from account inner join transaction on account.account_number=transaction.account_number where transaction_type in ('withdraw','deposit');

# 13. Find all accounts created by customers whose name starts with 'R'.
    select * from account where customer_name like'r%';

# 14. Retrieve customers sorted by their account balance in descending order.
    select customer_name, current_balance as desc_current_balance from account order by current_balance desc;

# 15. Display the average account balance per account type.
    select account_type ,avg(current_balance) as avg_balance from account group by account_type;

# CONCLUSION
The Banking Management System demonstrates fundamental banking operations using MySQL, providing a practical approach to managing customers, accounts, and transactions. It emphasizes database design, relational integrity, and the use of stored procedures for automation. While it is suitable for learning and small-scale simulations, it highlights the importance of accuracy, transparency, and structured data management in real-world banking. This project serves as a solid foundation for building more advanced banking applications with enhanced security, scalability, and user interfaces.
