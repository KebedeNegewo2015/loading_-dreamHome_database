# The purpose of creating this database is to implementing some SQL command including DML, DDL and.


```sql

CREATE DATABASE DreamHome;
```
use dreamhome;

## Creating Branch table

```sql
CREATE TABLE Branch (
branchNo varchar(10) PRIMARY KEY,
street varchar(40),
city varchar(30),
postcode varchar(20)
);
```
## Creating Staff Table

```sql
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
```
## Creating private Owner Table
```sql
CREATE TABLE PrivateOwner (
ownerNo varchar(10) PRIMARY KEY,
fName nvarchar(25),
lName nvarchar(25),
[Address] varchar(40),
telNo varchar(20)
);
```
## Creating Property For Rent Table 
```sql
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
```
## Creating Client Table
```sql
CREATE TABLE Client (
clientNo varchar(10) PRIMARY KEY,
fName nvarchar(20),
lName nvarchar(20),
telNo varchar(20),
prefType varchar(20),
maxRent numeric(6,2),
eMail varchar(40)
);
```
## Creating Viewing Table
```sql
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





# Insert datas to the Designed table and schema  I will show you how To insert Data
# to the existed table 


## query to inserting data's to the branch tabele
```sql
INSERT INTO Branch (branchNo, street, city, postcode)
VALUES
('B001', '123 Main St', 'Baltimore', 'MD 21201'),
('B002', '456 State St', 'Annapolis', 'MD 21401'),
('B003', '789 Park Ave', 'Rockville', 'MD 20850'),
('B004', '321 Vine St', 'Frederick', 'MD 21701'),
('B005', '555 Water St', 'Salisbury', 'MD 21801'),
('B006', '777 Main St', 'Cumberland', 'MD 21502'),
('B007', '888 State St', 'College Park', 'MD 20740'),
('B008', '222 Park Ave', 'Greenbelt', 'MD 20770'),
('B009', '333 Vine St', 'Hagerstown', 'MD 21740'),
('B010', '444 Water St', 'Laurel', 'MD 20707');
```
## query to inserting data's to the staff table

```sql
INSERT INTO Staff (staffNo, fName, lName, position, sex, DOB, salary, branchNo)
VALUES
('S001', 'John', 'Doe', 'Manager', 'M', '1980-01-01', 50000.00, 'B001'),
('S002', 'Jane', 'Doe', 'Assistant Manager', 'F', '1985-05-15', 40000.00, 'B001'),
('S003', 'Bob', 'Smith', 'Salesperson', 'M', '1990-03-10', 30000.00, 'B001'),
('S004', 'Sara', 'Lee', 'Salesperson', 'F', '1995-07-20', 30000.00, 'B001'),
('S005', 'Mike', 'Brown', 'Teller', 'M', '2000-11-30', 25000.00, 'B001'),
('S006', 'Lisa', 'Jones', 'Teller', 'F', '2005-09-25', 25000.00, 'B001'),
('S007', 'Tom', 'Wilson', 'Teller', 'M', '2010-12-05', 25000.00, 'B001'),
('S008', 'Karen', 'Davis', 'Teller', 'F', '2015-04-18', 25000.00, 'B001'),
('S009', 'David', 'Miller', 'Intern', 'M', '2020-02-01', 20000.00, 'B001'),
('S010', 'Jessica', 'Garcia', 'Intern', 'F', '2021-08-10', 20000.00, 'B001'),
('S011', 'John', 'Doe', 'Manager', 'M', '1980-05-15', 75000.00, 'B002'),
('S012', 'Jane', 'Smith', 'Salesperson', 'F', '1990-08-22', 45000.00, 'B002'),
('S013', 'Mike', 'Johnson', 'Accountant', 'M', '1985-11-03', 60000.00, 'B002'),
('S014', 'Emily', 'Davis', 'Teller', 'F', '1995-02-17', 35000.00, 'B002'),
('S015', 'David', 'Wilson', 'Teller', 'M', '1992-09-28', 35000.00, 'B002'),
('S016', 'John', 'Doe', 'Manager', 'M', '1980-05-15', 75000, 'B003'),
('S017', 'Jane', 'Smith', 'Assistant Manager', 'F', '1990-02-21', 50000, 'B003'),
('S018', 'David', 'Lee', 'Sales Representative', 'M', '1995-09-10', 40000, 'B003'),
('S019', 'Amy', 'Chen', 'Customer Representative', 'F', '1998-12-03', 35000, 'B003'),
('S020', 'Tom', 'Nguyen', 'Accountant', 'M', '1985-08-20', 60000, 'B003'),
('S021', 'John', 'Doe', 'Manager', 'M', '1980-01-01', 75000.00, 'B004'),
('S022', 'Jane', 'Doe', 'Assistant Manager', 'F', '1990-02-02', 50000.00, 'B004'),
('S023', 'Mark', 'Smith', 'Salesperson', 'M', '1995-03-03', 40000.00, 'B004'),
('S024', 'Lisa', 'Johnson', 'Salesperson', 'F', '1997-04-04', 40000.00, 'B004'),
('S025', 'David', 'Lee', 'Clerk', 'M', '2000-05-05', 30000.00, 'B004'),
('S026', 'John', 'Doe', 'Manager', 'M', '1980-05-15', 75000.00, 'B005'),
('S027', 'Jane', 'Smith', 'Salesperson', 'F', '1990-02-12', 50000.00, 'B005'),
('S028', 'Bob', 'Johnson', 'Clerk', 'M', '1995-07-20', 35000.00, 'B005'),
('S029', 'Emily', 'Davis', 'Clerk', 'F', '1997-01-01', 35000.00, 'B005'),
('S030', 'Tom', 'Williams', 'Salesperson', 'M', '1985-10-10', 50000.00, 'B005'),
('S031', 'Jack', 'Lee', 'Manager', 'M', '1978-03-25', 75000.00, 'B006'),
('S032', 'Lucy', 'Chen', 'Salesperson', 'F', '1991-06-30', 50000.00, 'B006'),
('S033', 'Mike', 'Wang', 'Clerk', 'M', '1996-11-18', 35000.00, 'B006'),
('S034', 'Linda', 'Zhang', 'Clerk', 'F', '1998-04-05', 35000.00, 'B006'),
('S035', 'David', 'Li', 'Salesperson', 'M', '1982-09-12', 50000.00, 'B006'),
('S036', 'John', 'Smith', 'Manager', 'M', '1980-05-15', 75000.00, 'B007'),
('S037', 'Emily', 'Jones', 'Assistant Manager', 'F', '1990-02-25', 50000.00, 'B007'),
('S038', 'Michael', 'Lee', 'Sales Representative', 'M', '1995-08-10', 40000.00, 'B007'),
('S039', 'Karen', 'Wang', 'Sales Representative', 'F', '1992-12-01', 40000.00, 'B007'),
('S040', 'David', 'Chen', 'Customer Service', 'M', '1997-04-20', 30000.00, 'B007'),
('S041', 'Sarah', 'Kim', 'Assistant Manager', 'F', '1991-11-05', 50000.00, 'B008'),
('S042', 'Brian', 'Park', 'Sales Representative', 'M', '1994-07-18', 40000.00, 'B008'),
('S043', 'Amanda', 'Nguyen', 'Customer Service', 'F', '1998-01-30', 30000.00, 'B008'),
('S044', 'Kevin', 'Tran', 'Sales Representative', 'M', '1993-03-12', 40000.00, 'B008'),
('S045', 'Eric', 'Song', 'Customer Service', 'M', '1996-09-23', 30000.00, 'B008'),
('S046', 'John', 'Doe', 'Manager', 'M', '1980-01-01', 75000.00, 'B009'),
('S047', 'Jane', 'Smith', 'Assistant Manager', 'F', '1985-05-05', 60000.00, 'B009'),
('S048', 'Michael', 'Brown', 'Salesperson', 'M', '1990-10-10', 45000.00, 'B009'),
('S049', 'Sarah', 'Johnson', 'Customer Service', 'F', '1995-02-15', 40000.00, 'B009'),
('S050', 'David', 'Lee', 'IT Specialist', 'M', '2000-06-20', 55000.00, 'B009'),
('S051', 'Emily', 'Wang', 'Manager', 'F', '1982-03-10', 80000.00, 'B010'),
('S052', 'Matthew', 'Garcia', 'Assistant Manager', 'M', '1987-07-15', 65000.00, 'B010'),
('S053', 'Ava', 'Rodriguez', 'Salesperson', 'F', '1992-11-20', 50000.00, 'B010'),
('S054', 'Ethan', 'Lopez', 'Customer Service', 'M', '1997-04-25', 45000.00, 'B010'),
('S055', 'Olivia', 'Gonzalez', 'IT Specialist', 'F', '2002-08-30', 60000.00, 'B010');
```
## query to inserting data's to the PrivateOwner table

```sql
INSERT INTO PrivateOwner (ownerNo, fName, lName, Address, telNo) VALUES
('101', 'John', 'Doe', '123 Main St', '555-1234'),
('102', 'Jane', 'Smith', '456 1st Ave', '555-5678'),
('103', 'Bob', 'Jones', '789 Elm St', '555-9101'),
('104', 'Mary', 'Brown', '234 Oak St', '555-1212'),
('105', 'Tom', 'Johnson', '567 Pine Ave', '555-1313'),
('106', 'Samantha', 'Garcia', '890 Maple St', '555-1414'),
('107', 'David', 'Lee', '1234 Cedar Rd', '555-1515'),
('108', 'Amy', 'Nguyen', '5678 Birch St', '555-1616'),
('109', 'Eric', 'Kim', '9012 Spruce Dr', '555-1717'),
('110', 'Jessica', 'Taylor', '3456 Walnut Ln', '555-1818'),
('111', 'Joshua', 'Rodriguez', '7890 Cedar Ave', '555-1919'),
('112', 'Emily', 'Martinez', '123 Elmwood Ave', '555-2020'),
('113', 'Daniel', 'Hernandez', '456 Oakwood Rd', '555-2121'),
('114', 'Ava', 'Lopez', '789 Pine Ln', '555-2222'),
('115', 'Tyler', 'Gonzalez', '234 Maple Ave', '555-2323'),
('116', 'Sophia', 'Perez', '567 Cedar Rd', '555-2424'),
('117', 'Ethan', 'Rivera', '890 Birch St', '555-2525'),
('118', 'Isabella', 'Morgan', '1234 Spruce Dr', '555-2626'),
('119', 'Mason', 'Bell', '5678 Walnut Ln', '555-2727'),
('120', 'Mia', 'Reed', '9012 Elmwood Ave', '555-2828'),
('121', 'Noah', 'Harris', '3456 Oakwood Rd', '555-2929'),
('122', 'Chloe', 'Clark', '7890 Pine Ln', '555-3030'),
('123', 'Oliver', 'Lewis', '123 Maple Ave', '555-3131'),
('124', 'Aria', 'Robinson', '456 Cedar Rd', '555-3232'),
('125', 'Lucas', 'Walker', '789 Birch St', '555-3333'),
('126', 'Lila', 'Parker', '1234 Spruce Dr', '555-3434'),
('127', 'Alexander', 'Cook', '5678 Walnut Ln', '555-3535'),
('128', 'Aaliyah', 'Edwards', '9012 Elmwood Ave', '555-3636'),
('129', 'Caleb', 'Bailey', '3456 Oakwood Rd', '555-3737'),
('130', 'Ellie', 'Cooper', '7890 Pine Ln', '555-3838'),
('131', 'Luke', 'Richardson', '123 Maple Ave', '555-3939'),
('132', 'Harper', 'Wood', '456 Cedar Rd', '555-4040'),
('133', 'Gabriel', 'Watson', '789 Birch St', '555-4141');
```

## query to inserting data's to the PropertyForRent table
```sql
INSERT INTO PropertyForRent (propertyNo, street, city, postcode, type, rooms, rent, ownerNo, staffNo, branchNo)
VALUES
('P001', '123 Main St', 'Baltimore', '21201', 'Apartment', 2, 120.00, '101', 'S001', 'B001'),
('P002', '456 Elm St', 'Annapolis', '21401', 'House', 3, 180, '102', 'S002', 'B002'),
('P003', '789 Oak St', 'Rockville', '20850', 'Apartment', 1, 800, '103', 'S003', 'B003'),
('P004', '321 Maple Ave', 'Frederick', '21701', 'House', 4, 250, '104', 'S004', 'B004'),
('P005', '654 Walnut St', 'Salisbury', '21801', 'Apartment', 2, 110, '105', 'S005', 'B001'),
('P006', '987 Pine St', 'Cumberland', '21502', 'House', 3, 190, '106', 'S006', 'B002'),
('P007', '135 Birch Ave', 'College Park', '20740', 'Apartment', 1, 900, '107', 'S007', 'B003'),
('P008', '864 Chestnut St', 'Greenbelt', '20770', 'House', 4, 280, '108', 'S008', 'B004'),
('P009', '246 Spruce Ave', 'Hagerstown', '21740', 'Apartment', 2, 125, '109', 'S009', 'B001'),
('P010', '579 Cedar St', 'Laurel', '20707', 'House', 3, 200, '110', 'S010', 'B002'),
('P011', '111 Main St', 'Baltimore', '21202', 'Apartment', 1, 950, '101', 'S001', 'B003'),
('P012', '222 Elm St', 'Annapolis', '21403', 'House', 4, 270, '102', 'S002', 'B004'),
('P013', '333 Oak St', 'Rockville', '20852', 'Apartment', 2, 140, '103', 'S003', 'B001'),
('P014', '444 Maple Ave', 'Frederick', '21702', 'House', 3, 220, '104', 'S004', 'B002'),
('P015', '555 Walnut St', 'Salisbury', '21802', 'Apartment', 1, 100, '105', 'S005', 'B003'),
('P016', '666 Pine St', 'Cumberland', '21503', 'House', 4, 300, '106', 'S006', 'B004'),
('P017', '777 Birch Ave', 'College Park', '20741', 'Apartment', 2, 130, '107', 'S007', 'B001'),
('P018', '888 Chestnut St', 'Greenbelt', '20771', 'House', 3, 240, '108', 'S008', 'B002'),
('P019', '123 Main St', 'Baltimore', 'MD 21201', 'Apartment', 2, 120.00, '111', 'S012', 'B005'),
('P020', '456 Elm St', 'Annapolis', 'MD 21401', 'House', 4, 200.00, '112', 'S020', 'B006'),
('P021', '789 Oak St', 'Rockville', 'MD 20850', 'Condo', 3, 150.00, '113', 'S012', 'B007'),
('P022', '111 Pine St', 'Frederick', 'MD 21701', 'House', 5, 250.00, '114', 'S020', 'B008'),
('P023', '222 Maple St', 'Salisbury', 'MD 21801', 'Apartment', 1, 800.00, '115', 'S012', 'B005'),
('P024', '333 Cedar St', 'Cumberland', 'MD 21502', 'Condo', 2, 100.00, '116', 'S020', 'B006'),
('P025', '444 Spruce St', 'College Park', 'MD 20740', 'House', 3, 180.00, '117', 'S012', 'B007'),
('P026', '555 Birch St', 'Greenbelt', 'MD 20770', 'Apartment', 2, 120.00, '118', 'S020', 'B008'),
('P027', '666 Oak St', 'Hagerstown', 'MD 21740', 'Condo', 1, 900.00, '119', 'S012', 'B005'),
('P028', '777 Maple St', 'Laurel', 'MD 20707', 'House', 4, 220.00, '120', 'S020', 'B006'),
('P029', '888 Pine St', 'Baltimore', 'MD 21202', 'Apartment', 2, 110.00, '111', 'S012', 'B007'),
('P030', '999 Elm St', 'Annapolis', 'MD 21403', 'Condo', 3, 160.00, '112', 'S020', 'B008'),
('P031', '111 Oak St', 'Rockville', 'MD 20851', 'House', 4, 200.00, '113', 'S012', 'B005'),
('P032', '222 Pine St', 'Frederick', 'MD 21702', 'Apartment', 1, 800.00, '114', 'S020', 'B006'),
('P033', '333 Maple St', 'Salisbury', 'MD 21802', 'Condo', 2, 100.00, '115', 'S012', 'B007'),
('P034', '444 Cedar St', 'Cumberland', 'MD 21503', 'House', 3, 180.00, '116', 'S020', 'B008'),
('P035', '555 Spruce St', 'College Park', 'MD 20741', 'Apartment', 2, 120.00, '117', 'S012', 'B005'),
('P036', '123 Main St', 'Baltimore', 'MD 21201', 'Apartment', 2, 120, '121', 'S021', 'B007'),
('P037', '456 Elm St', 'Annapolis', 'MD 21401', 'House', 3, 180, '122', 'S030', 'B008'),
('P038', '789 Oak St', 'Rockville', 'MD 20850', 'Condo', 2, 150, '123', 'S021', 'B007'),
('P039', '111 Pine St', 'Frederick', 'MD 21701', 'Apartment', 1, 900, '124', 'S030', 'B008'),
('P040', '222 Cedar St', 'Salisbury', 'MD 21801', 'House', 4, 220, '125', 'S021', 'B009'),
('P041', '333 Maple St', 'Cumberland', 'MD 21502', 'Condo', 2, 140, '126', 'S030', 'B010'),
('P042', '444 Birch St', 'College Park', 'MD 20740', 'Apartment', 1, 100, '127', 'S021', 'B009'),
('P043', '555 Ash St', 'Greenbelt', 'MD 20770', 'House', 3, 170, '128', 'S030', 'B010'),
('P044', '666 Walnut St', 'Hagerstown', 'MD 21740', 'Condo', 2, 130, '129', 'S021', 'B007'),
('P045', '777 Chestnut St', 'Laurel', 'MD 20707', 'Apartment', 2, 110, '130', 'S030', 'B008'),
('P046', '234 Oak Ln', 'Baltimore', 'MD 21202', 'House', 4, 240, '121', 'S021', 'B007'),
('P047', '567 Maple Ln', 'Annapolis', 'MD 21403', 'Condo', 2, 160, '122', 'S030', 'B008'),
('P048', '890 Cedar Ln', 'Rockville', 'MD 20851', 'Apartment', 1, 950, '123', 'S021', 'B007'),
('P049', '123 Pine Ln', 'Frederick', 'MD 21702', 'House', 3, 190, '124', 'S030', 'B008'),
('P050', '456 Cedar Ln', 'Salisbury', 'MD 21802', 'Condo', 2, 130, '125', 'S021', 'B009'),
('P051', '789 Elm Ln', 'Cumberland', 'MD 21503', 'Apartment', 1, 850, '126', 'S030', 'B010'),
('P052', '111 Birch Ln', 'College Park', 'MD 20741', 'House', 4, 230, '127', 'S021', 'B009');
```
## query to inserting data's to the client table

```sql
INSERT INTO Client (clientNo, fName, lName, telNo, prefType, maxRent, eMail)
VALUES
('C001', 'John', 'Doe', '1234567890', 'Apartment', 1500.00, 'johndoe@email.com'),
('C002', 'Jane', 'Smith', '2345678901', 'House', 2000.00, 'janesmith@email.com'),
('C003', 'David', 'Lee', '3456789012', 'Condo', 1800.00, 'davidlee@email.com'),
('C004', 'Sarah', 'Johnson', '4567890123', 'Apartment', 1200.00, 'sarahjohnson@email.com'),
('C005', 'Michael', 'Brown', '5678901234', 'Townhouse', 2200.00, 'michaelbrown@email.com'),
('C006', 'Karen', 'Davis', '6789012345', 'House', 2500.00, 'karendavis@email.com'),
('C007', 'William', 'Wilson', '7890123456', 'Condo', 1600.00, 'williamwilson@email.com'),
('C008', 'Amy', 'Garcia', '8901234567', 'Apartment', 1400.00, 'amygarcia@email.com'),
('C009', 'Christopher', 'Rodriguez', '9012345678', 'Townhouse', 2400.00, 'christopherrodriguez@email.com'),
('C010', 'Megan', 'Lopez', '0123456789', 'Condo', 1900.00, 'meganlopez@email.com'),
('C011', 'Daniel', 'Hernandez', '2345678901', 'House', 2300.00, 'danielhernandez@email.com'),
('C012', 'Stephanie', 'Gonzalez', '3456789012', 'Apartment', 1300.00, 'stephaniegonzalez@email.com'),
('C013', 'Ryan', 'Perez', '4567890123', 'Condo', 1700.00, 'ryanperez@email.com'),
('C014', 'Emily', 'Torres', '5678901234', 'Townhouse', 2000.00, 'emilytorres@email.com'),
('C015', 'Joshua', 'Rivera', '6789012345', 'House', 2500.00, 'joshuarivera@email.com'),
('C016', 'Alyssa', 'Collins', '7890123456', 'Apartment', 1400.00, 'alyssacollins@email.com'),
('C017', 'Kevin', 'Bell', '8901234567', 'Townhouse', 2200.00, 'kevinbell@email.com'),
('C018', 'Hannah', 'Murphy', '9012345678', 'Condo', 1900.00, 'hannahmurphy@email.com'),
('C019', 'Brandon', 'Cook', '0123456789', 'Apartment', 1200.00, 'brandoncook@email.com'),
('C020', 'Lauren', 'Bailey', '2345678901', 'House', 2300.00, 'laurenbailey@email.com');
```
## query to inserting data's to the viewing table

```sql
INSERT INTO Viewing (clientNo, propertyNo, viewDate, comment)
VALUES
('C001', 'P001', '2022-01-01 10:00:00', 'Nice property'),
('C002', 'P002', '2022-01-02 11:00:00', 'Spacious rooms'),
('C003', 'P003', '2022-01-03 12:00:00', 'Good location'),
('C004', 'P004', '2022-01-04 13:00:00', 'Modern design'),
('C005', 'P005', '2022-01-05 14:00:00', 'Great views'),
('C006', 'P006', '2022-01-06 15:00:00', 'Quiet neighborhood'),
('C007', 'P007', '2022-01-07 16:00:00', 'Close to amenities'),
('C008', 'P008', '2022-01-08 17:00:00', 'Convenient location'),
('C009', 'P009', '2022-01-09 18:00:00', 'Cozy and comfortable'),
('C010', 'P010', '2022-01-10 19:00:00', 'Good value for money'),
('C011', 'P011', '2022-01-11 10:00:00', 'Modern amenities'),
('C012', 'P012', '2022-01-12 11:00:00', 'Bright and airy'),
('C013', 'P013', '2022-01-13 12:00:00', 'Well-maintained property'),
('C014', 'P014', '2022-01-14 13:00:00', 'Spacious living area'),
('C015', 'P015', '2022-01-15 14:00:00', 'Great location'),
('C016', 'P016', '2022-01-16 15:00:00', 'Nice neighborhood'),
('C017', 'P017', '2022-01-17 16:00:00', 'Close to public transportation'),
('C018', 'P018', '2022-01-18 17:00:00', 'Pet-friendly'),
('C019', 'P019', '2022-01-19 18:00:00', 'Ideal for families'),
('C020', 'P020', '2022-01-20 19:00:00', 'Good security features'),
('C001', 'P021', '2022-01-01 10:00:00', 'Great property with spacious rooms.'),
('C002', 'P022', '2022-01-02 11:00:00', 'Lovely apartment with a great view.'),
('C003', 'P023', '2022-01-03 12:00:00', 'Cozy and well-maintained property.'),
('C004', 'P024', '2022-01-04 13:00:00', 'Great location with good amenities.'),
('C005', 'P025', '2022-01-05 14:00:00', 'Spacious rooms and modern interiors.'),
('C006', 'P026', '2022-01-06 15:00:00', 'Nice property with a great balcony.'),
('C007', 'P027', '2022-01-07 16:00:00', 'Clean and well-kept property.'),
('C008', 'P028', '2022-01-08 17:00:00', 'Great property with a beautiful garden.'),
('C009', 'P029', '2022-01-09 18:00:00', 'Lovely apartment with good facilities.'),
('C010', 'P030', '2022-01-10 19:00:00', 'Spacious and modern property.'),
('C011', 'P021', '2022-01-11 10:00:00', 'Great location and good amenities.'),
('C012', 'P022', '2022-01-12 11:00:00', 'Cozy and well-maintained property.'),
('C013', 'P023', '2022-01-13 12:00:00', 'Great property with a nice view.'),
('C014', 'P024', '2022-01-14 13:00:00', 'Lovely property with spacious rooms.'),
('C015', 'P025', '2022-01-15 14:00:00', 'Nice apartment with modern interiors.'),
('C016', 'P026', '2022-01-16 15:00:00', 'Well-kept property with a nice balcony.'),
('C017', 'P027', '2022-01-17 16:00:00', 'Beautiful property with good facilities.'),
('C018', 'P028', '2022-01-18 17:00:00', 'Spacious property with a lovely garden.'),
('C019', 'P029', '2022-01-19 18:00:00', 'Clean and well-maintained apartment.'),
('C020', 'P030', '2022-01-20 19:00:00', 'Modern property with a great location.'),
('C001', 'P031', '2021-01-01 10:00:00', 'Liked the location'),
('C002', 'P032', '2021-01-02 11:00:00', 'Small kitchen'),
('C003', 'P033', '2021-01-03 12:00:00', 'Noisy street'),
('C004', 'P034', '2021-01-04 13:00:00', 'Great view'),
('C005', 'P035', '2021-01-05 14:00:00', 'Loved the garden'),
('C006', 'P036', '2021-01-06 15:00:00', 'Too far from work'),
('C007', 'P037', '2021-01-07 16:00:00', 'Good size rooms'),
('C008', 'P038', '2021-01-08 17:00:00', 'Needs some repairs'),
('C009', 'P039', '2021-01-09 18:00:00', 'Beautifully decorated'),
('C010', 'P040', '2021-01-10 19:00:00', 'Too expensive'),
('C011', 'P041', '2021-01-11 10:00:00', 'Good location'),
('C012', 'P042', '2021-01-12 11:00:00', 'Close to public transportation'),
('C013', 'P043', '2021-01-13 12:00:00', 'Too small for family'),
('C014', 'P044', '2021-01-14 13:00:00', 'Great natural light'),
('C015', 'P045', '2021-01-15 14:00:00', 'Liked the layout'),
('C016', 'P046', '2021-01-16 15:00:00', 'Needs more storage'),
('C017', 'P047', '2021-01-17 16:00:00', 'Quiet neighborhood'),
('C018', 'P048', '2021-01-18 17:00:00', 'Not pet-friendly'),
('C019', 'P049', '2021-01-19 18:00:00', 'Great location'),
('C020', 'P050', '2021-01-20 19:00:00', 'Loved the kitchen design');
```
