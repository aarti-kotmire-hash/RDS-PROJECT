
````markdown
# Employee Management System (AWS RDS + EC2 + MySQL) #

## Overview ##
This project demonstrates a simple Employee Management System hosted on AWS RDS (MySQL) and accessed via an EC2 Ubuntu instance.  
It covers cloud database setup, secure connectivity, SQL queries, and practical use cases.



##  Technologies Used ##
- AWS RDS (MySQL) – Database hosting  
- AWS EC2 (Ubuntu) – Client environment  
- MySQL Client – Query execution  
- SQL – Employee database schema & queries  
- Linux (Ubuntu) – Configuration & setup  



##  Setup Steps ##

# 1️ Launch RDS Instance #
- Engine: MySQL
- Free Tier eligible  
- Publicly accessible: Yes (or restrict via EC2 security group)  
- Note the Endpoint and Port (3306)


# 2️ Launch EC2 Instance #
- OS: Ubuntu 22.04 LTS
- Install MySQL client:
sudo apt update && sudo apt install mysql-client -y


# 3️ Connect EC2 → RDS #
mysql -h <RDS-ENDPOINT> -P 3306 -u admin -p


# 4 Database Schema #
CREATE DATABASE employee_db;
USE employee_db;


# 5 Create Table #
CREATE TABLE Employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);


# 6 Sample Data #
INSERT INTO Employees (name, department, salary) VALUES
('AARTI', 'HR', 50000),
('ROHAN', 'IT', 40000),
('SNEHA', 'FINANCE', 60000),
('AMIT', 'IT', 50000),
('NEHA', 'HR', 45000);



# 6 SQL Queries #
1. Show all employees
SELECT * FROM Employees;


2. Only IT employees
SELECT Name, Salary FROM Employees WHERE Department='IT';


3. Average salary by department
SELECT Department, AVG(Salary) AS AvgSalary FROM Employees GROUP BY Department;


4. Highest paid employee
SELECT Name, Salary FROM Employees ORDER BY Salary DESC LIMIT 1;



##  Output Sample  ##

+--------+-------------+----------+
| NAME   | DEPARTMENT  | SALARY   |
+--------+-------------+----------+
| AARTI  | HR          | 50000.00 |
| ROHAN  | IT          | 40000.00 |
| SNEHA  | FINANCE     | 60000.00 |
| AMIT   | IT          | 50000.00 |
| NEHA   | HR          | 45000.00 |
+--------+-------------+----------+



##  Learning Outcomes  ##

1. Hands-on experience with **AWS RDS & EC2**
2. Designed relational schema with **primary & foreign keys**
3. Executed **SQL queries for CRUD & analytics**
4. Deployed a **cloud-based employee management system**



##  Author  ## 

AARTI KOTMIRE

*  GitHub: https://github.com/aarti-kotmire-hash/RDS-PROJECT
*  Email: aartikotmire123@gmail.com






 

