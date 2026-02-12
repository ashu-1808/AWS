Here are your notes written **as it is from the images** 👇

---

# RDS (Relational Database Service)

* RDS is a fully managed relational database service from Amazon that makes it easy to setup, operate and scale relational databases in the cloud.

---

## What is meant by data?

→ Data is collection of raw facts, figures, symbols or observations.

---

## Database?

→ Database is a systematic collection of data.

Eg:

MT → 204006
MT → M.Tech
20 → 2020 year
40 → CSE department
06 → Roll no.

---

## DBMS?

→ Database Management System is a software that allows you to create, define, manipulate and manage database.

### Types of DBMS

1. Hierarchical DBMS → Tree structure
2. Network DBMS → Graph structure
3. Relational DBMS → Tables (Rows and Columns)
4. Object oriented DBMS → Objects & Classes

---

## RDBMS (Relational Database Management System)

→ It is a software or applications that manages and controls data stored in tabular form.

---

# Table

Table is a collection of related data in organized manner in the form of rows and columns.

---

### Tables

* Tables are related to each others
* All fields must be filled
* Data is filled in the form of rows & columns
* A row of table is also called record/tuple
* It contains specific information of each individual entry in the table
* Column of table is also called attribute/field
* Each table has its own primary key
* A schema is used to strictly define table columns, index and relation between tables
* Best suitable for online transaction process (OLTP)
* Cannot scale out horizontally because tables are related to each other
* But we can scale out vertically

---

## Famous RDBMS

→ MySQL, Oracle, MariaDB, IBM-DB2

---

# RDBMS vs NoSQL

| Feature     | RDBMS                     | NoSQL                     |
| ----------- | ------------------------- | ------------------------- |
| Query lang  | SQL                       | API                       |
| Consistency | Strong (ACID)             | BASE                      |
| Best for    | Complex queries data      | High volume / Low latency |
| Use case    | Banking / ERP / Reporting | Big data / Real time apps |
| Complexity  | Structured & strict       | Flexible / schema-less    |
| Scalability | Vertical (Scale up)       | Horizontal (Scale out)    |
| Schema      | Fixed (Pre-defined)       | Flexible                  |
| Data model  | Table (Rows & Columns)    | Document, Column, Graph   |

---
Here are your notes written **as it is from the image** 👇

---

# AWS provides Relational Database Service

* AWS RDS is a fully managed AWS service
* It is fully responsible for DB automated group

  1. Security group
  2. Software updates for DB
  3. AWS provides Disaster recovery

---

### Multi AZ

(AZ-1)
Primary Database – Standalone

(AZ-2)
Clone database – Standby

---

5. By default, every DB has weekly maintenance window of (1–35 days) can be created manually.

---

There are some settings managed by users:

1. Managed DB instances
2. Creation of relational database schema or design of database

---

There are 8 Relational Database options on AWS:

1. Aurora (MySQL – compatible)
2. Aurora (PostgreSQL – compatible)
3. MySQL
4. PostgreSQL
5. Maria DB
6. Oracle Database
7. Microsoft SQL Server
8. IBM DB2

---
Here are your notes written **as it is from the image** 👇

---

## Steps for RDS

1. Select **Standard create**
2. Choose **Engine option and its version**
3. Give **Database name (console-name)**
   Master username **admin** & master-password
4. Choose **Storage**
5. Choose **Availability and durability**
   (Gives option to create standby instance)

---

## 6. Connectivity

i. Choose if you want to connect it to EC2 or not
ii. Check network type
iii. Choose VPC or get default
iv. Public access or not
v. VPC security group → **RDS-security** (if not there then create it)

---

## Imp (Additional configuration)

i. Give database name (**Real-database-name**) → **DB-1**
ii. Backup option or Backup replication
iii. Maintenance option


---

## 7) Go to RDS Security Group & Edit Inbound Rules

Add:

1. MySQL/Aurora → Anywhere → Port: **3306**
2. SSH → Anywhere → **22**
3. HTTP → Anywhere → **80**
4. HTTPS → Anywhere → **443**
5. Custom TCP → Anywhere → **8080**

---

## 8) Connect Ubuntu Instance

```
sudo -i
apt install mysql-client -y
mysql -h <endpoint of database> -u admin -p
```

Enter password

```
mysql> create database student_db;
mysql> exit
```

(DB-1)

---

## Backend Setup

```
git clone https://github.com/shubhamkalgat/cloudblitz-student-app.git
cd cloudblitz-student-app
cd backend
apt install openjdk-17-jdk -y
java --version
apt install maven -y
mvn --version
mvn clean
```

---

## To connect backend to frontend

```
vim src/main/resources/application.properties
```

Press `i` → To enter insert mode

Edit localhost with endpoint of database:

```
spring.datasource.url=jdbc:mariadb://<database-endpoint>:3306/student_db
```

Press `Esc` → `:wq`

---
Here are your notes written **as it is from the image** 👇

---

## Spring Datasource

* spring.datasource.username = admin
* spring.datasource.password = abcd1234
* press **Esc** then press `:wq` to save & exit

---

## Build

* `mvn clean package`  *(It will build code)*
* Build success

---

## Install NodeJS

* `apt install nodejs npm -y`
* `npm install`  *(Node package manager)*

---

## To connect frontend to backend

* `vim .env`
* Change URL with instance public URL

Example:

```
http://49.503.504.31:8080/api
```

* `esc` then `:wq` to save & exit
* `npm run build`

---

## Install Apache Webserver

* `apt install apache2 -y`

---

## Copy whole dist folder in web server

```
cp -rf dist/* /var/www/html/
```

---

## Start Apache

```
systemctl start apache2
systemctl enable apache2
```

---
Here are your notes written **as it is from the image** 👇

---

```
cd ..
cd backend
cd target
java -jar student-registration-backend-0.0.1-SNAPSHOT.jar
```

e.g. `java -jar student-registration-backend-0.0.1-SNAPSHOT.jar`

* open public URL of instance in browser
* Add entries
* keep the old instance running
* open the same instance on different windows

---

```
sudo -i
mysql -h (Endpoint of Database) -u admin -p
```

* Enter password
* show databases;
* use student_db;
* show tables;
* select * from users;

---

While doing this:

We need to install java's updated version, because while installing apt may install the previous version.

We install maven → It helps to build code.

---
