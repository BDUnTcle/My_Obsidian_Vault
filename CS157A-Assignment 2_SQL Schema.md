---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---


# Relational Schema
## 2 Entities
1. Department
2. Employees
## Table Design
### Department table:
Attribute 1: department_id (INT, PRIMARY KEY)
Attribute 1: department_name (VARCHAR)
Attribute 3: department_location (VARCHAR)
```mysql
CREATE TABLE Departments(
	department_id INT PRIMARY KEY,
	department_name VARCHAR(255),
	department_location VARCHAR(255)
);
```
### Employee table:
Attribute 1: employee_id (INT, PRIMARY KEY)
Attribute 2: employee_name (VARCHAR)
Attribute 3: employee_title (VARCHAR)
Attribute 4: employee_salary (INT)
Attribute 5: employee_hiring_date (DATE)
Attribute 6: department_id (FOREIGN KEY -> department table)
```mysql
CREATE TABLE Employees(
	employee_id INT PRIMARY KEY,
	employee_name VARCHAR(100) NOT NULL,
	employee_title VARCHAR(255),
	employee_salary INT,
	employee_hiring_date DATE,
	department_id INT,
	FOREIGN KEY(department_id) REFERENCES Departments(department_id)
);
```
---
# Code
```python
from lxml import etree
import mysql.connector
db_config = {
    'host': 'localhost',
    'user': 'root',
    'password': '925821'
}
# connect to mysql server
server_conn = mysql.connector.connect(**db_config)
server_cursor = server_conn.cursor()
# create database
server_cursor.execute(f"CREATE DATABASE IF NOT EXISTS CS157A_HW2")
print(f"Database Created !")
# create tables
server_cursor.execute(f"USE CS157A_HW2")
server_cursor.execute(f"CREATE TABLE IF NOT EXISTS Departments(department_id INT PRIMARY KEY,department_name VARCHAR(255),department_location VARCHAR(255))")
server_cursor.execute(f"CREATE TABLE IF NOT EXISTS Employees(employee_id INT PRIMARY KEY,employee_name VARCHAR(100) NOT NULL,employee_title VARCHAR(255),employee_salary INT,employee_hiring_date DATE,department_id INT,FOREIGN KEY(department_id) REFERENCES Departments(department_id))")

file_path = "dataset.xml"
tree = etree.parse(file_path)
root = tree.getroot()
# parse xml and insert 
for department in root.xpath("//department"):
    department_id = department.get("id")
    name = department.findtext("name")
    location = department.findtext("location")
    print(f"Department ID: {department_id}, Name: {name}, Location: {location}")
    server_cursor.execute("INSERT INTO Departments(department_id,department_name,department_location) VALUES (%s,%s,%s)"
                          ,(department_id,name,location))
    employees = department.find("employees").findall("employee")

    for employee in employees:
        employee_id = employee.findtext("id")
        employee_name = employee.findtext("name")
        employee_title = employee.findtext("title")
        employee_salary = employee.findtext("salary")
        employee_hire_date = employee.findtext("hire_date")
        print(f"  Employee ID: {employee_id}, Name: {employee_name}, Title: {employee_title}, "
               f"Salary: {employee_salary}, Hire Date: {employee_hire_date}")
        server_cursor.execute("INSERT INTO Employees(employee_id,employee_name,employee_title,employee_salary,employee_hiring_date,department_id) VALUES (%s,%s,%s,%s,%s,%s)"
                              ,(employee_id,employee_name,employee_title,employee_salary,employee_hire_date,department_id))
# commit changes and close connection
server_conn.commit()
server_cursor.close()
server_conn.close()
```
---
# Screen Shots
![[screen shoot_0 1.png|500]] 
![[screen shoot_1 1.png|500]]
![[screen shoot_2 1.png|500]]