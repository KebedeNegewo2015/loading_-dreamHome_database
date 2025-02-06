# The purpose of creating this database is to implementing some SQL command including DML, DDL and.


```sql

CREATE DATABASE DreamHome;

use dreamhome;

## Creating Branch table

CREATE TABLE Branch (
branchNo varchar(10) PRIMARY KEY,
street varchar(40),
city varchar(30),
postcode varchar(20)
);

CREATE TABLE Staff (
staffNo varchar(10) PRIMARY KEY,
fName nvarchar(25),
lName nvarchar(25),
position varchar(40),
sex char(1),
DOB datetime,
salary numeric(8,2),
branchNo varchar(10) FOREIGN KEY REFERENCES Branch
);

CREATE TABLE PrivateOwner (
ownerNo varchar(10) PRIMARY KEY,
fName nvarchar(25),
lName nvarchar(25),
[Address] varchar(40),
telNo varchar(20)
);

CREATE TABLE PropertyForRent (
propertyNo varchar(10) PRIMARY KEY,
street varchar(30),
city varchar(30),
postcode varchar(20),
type varchar(20) not null,
rooms numeric(2) default 4,
rent numeric(5,2) default 0,
ownerNo varchar(10) FOREIGN KEY REFERENCES PrivateOwner,
staffNo varchar(10) FOREIGN KEY REFERENCES Staff,
branchNo varchar(10) FOREIGN KEY REFERENCES Branch
);

CREATE TABLE Client (
clientNo varchar(10) PRIMARY KEY,
fName nvarchar(20),
lName nvarchar(20),
telNo varchar(20),
prefType varchar(20),
maxRent numeric(6,2),
eMail varchar(40)
);

CREATE TABLE Viewing (
clientNo varchar(10)
  constraint clientNo_fk FOREIGN KEY(clientNo) REFERENCES Client,
propertyNo varchar(10)
  FOREIGN KEY REFERENCES PropertyForRent,
viewDate datetime,
comment varchar(100),
constraint viewing_pk PRIMARY KEY(clientNo,propertyNo)
);

```
