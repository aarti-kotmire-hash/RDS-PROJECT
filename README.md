RDS-PROJECT

Employees Management System (AWS RDS + EC2 + SQL)


Project Overview
This project demonstrates the deployment of an Employee Management System on AWS Cloud using MySQL Database (Amazon RDS) and an EC2 instance.  
The goal of this project is to understand cloud database deployment, connectivity between RDS and EC2, and execution of SQL queries using Oracle SQL Developer.


The project demonstrates how to design and manage an Employee Management System using

A) AWS SERVICES USED
        1.	Amazon RDS – MySQL Database deployment  
        2.	Amazon EC2 – Windows/Linux instance for database connectivity  
        3.	Security Groups – For configuring inbound rules (port access)  
        4.	MySQL Client – For managing and executing SQL queries
   

B) TECH STACK
        1.	AWS RDS → MySQL (Free Tier)
        2.	AWS EC2 → Amazon Linux 2 (Free Tier)
        3.	SQL → Database schema & queries
   

C) SETUP STEPS
1) Create RDS Database
        a)	Engine: MySQL (Free Tier)
        b)	DB Name: Employee-db
        c)	Username: admin
        d)	Password: ****
        e)	Connectivity: Public access (Yes, for testing)

2) Create EC2 Instance
        a)	Instance Type: t2.micro (Free Tier)
        b)	Security Group: 
              SSH (22) → Allow your IP
              MySQL (3306) → Allow RDS connection

3) Connect EC2 to RDS
        Step 1 - Login to EC2
              ssh -i “my-key.pem” ubuntu@your-ec2-public-ip  
        Step 2 - Install MySQL client
              sudo yum install -y mysql  
        Step 3 - Connect to RDS
              mysql -h <RDS-ENDPOINT> -u admin -p
                  h = RDS endpoint
                  P = port (default 3306)
                  u = username (admin)
                  p = password
   

D) CREATE DATABASE
          CREATE DATABASE
          CREATE DATABASE EmployeeDB;
          USE EmployeeDB;
          

E) CREATE TABLE
          CREATE TABLE Employees (
          Name VARCHAR(100),
          Department VARCHAR(50),
          Salary DECIMAL(10,2));
          

F) INSERT DATA
        INSERT INTO Employees (Name, Department, Salary)
        VALUES
        ('AARTI', 'HR', 40000),
        ('ROHAN', 'IT', 55000),
        ('SNEHA', 'FINANCE', 60000),
        ('AMIT', 'IT', 50000),
        ('NEHA', 'HR', 45000);
        

G) QURIES RUN
Show all employees:
        SELECT * FROM Employees;
        
Only IT employees:
        SELECT Name, Salary FROM Employees WHERE Department='IT';

Average salary by department:
        SELECT Department, AVG(Salary) AS AvgSalary FROM Employees GROUP BY Department;

Highest paid employee:
        SELECT Name, Salary FROM Employees ORDER BY Salary DESC;
        


H) EXIT MYSQL
        exit;

      


OUTPUT SAMPLE:

mysql> SELECT * FROM EMPLOYEES;
+-------+------------+----------+
| NAME  | DEPARTMENT | SALARY   |
+-------+------------+----------+
| AARTI | HR         | 50000.00 |
| ROHAN | IT         | 40000.00 |
| SNEHA | FINANCE    | 60000.00 |
| AMIT  | IT         | 50000.00 |
| NEHA  | HR         | 45000.00 |
+-------+------------+----------+
5 rows in set (0.00 sec)

mysql> SELECT NAME, SALARY FROM EMPLOYEES WHERE DEPARTMENT='IT';
+-------+----------+
| NAME  | SALARY   |
+-------+----------+
| ROHAN | 40000.00 |
| AMIT  | 50000.00 |
+-------+----------+
2 rows in set (0.00 sec)

mysql> SELECT DEPARTMENT, AVG(SALARY) AS AVGSALARYY FROM EMPLOYEES GROUP BY DEPARTMENT;
+------------+--------------+
| DEPARTMENT | AVGSALARYY   |
+------------+--------------+
| HR         | 47500.000000 |
| IT         | 45000.000000 |
| FINANCE    | 60000.000000 |
+------------+--------------+
3 rows in set (0.00 sec)

mysql> SELECT NAME, SALARY FROM EMPLOYEES ORDER BY SALARY DESC;
+-------+----------+
| NAME  | SALARY   |
+-------+----------+
| SNEHA | 60000.00 |
| AARTI | 50000.00 |
| AMIT  | 50000.00 |
| NEHA  | 45000.00 |
| ROHAN | 40000.00 |
+-------+----------+
5 rows in set (0.00 sec)


LEARNING OUTCOMES
        1.	Hands-on experience with AWS RDS & EC2
        2.	Designed relational schema with primary & foreign keys
        3.	Executed SQL queries for data analysis
        4.	Deployed a cloud-based student management system

