
### the qeuries and the er diagram and the schema in `DATABASEPROJECT.md`
## first :

restore `Talkha Car Agency` 

 it is the initial requirements before the update.

it if filled with this moch data ,
 ``` sql
 CREATE TABLE Client
(
  ClientID INT PRIMARY KEY,
  Fname varchar(20) NOT NULL,
  Lname varchar(20) NOT NULL,
  Email varchar(40) NOT NULL,
  Street varchar(20) NOT NULL,
  City varchar(20) ,
);

CREATE TABLE Salesperson
(
  SalespersonID INT  PRIMARY KEY ,
  Fname varchar(20) NOT NULL,
  Lname varchar(20) NOT NULL,
  Email varchar(20) NOT NULL,
  Work_hours INT NOT NULL,
);

CREATE TABLE Sale
(
  SaleiD INT PRIMARY KEY,
  Date varchar(20) NOT NULL,
  Price float NOT NULL,
  paymentMethod varchar(40) ,
  AdditionalFees float ,
  SalespersonID INT,
  ClientID INT,
  FOREIGN KEY (SalespersonID) REFERENCES Salesperson(SalespersonID),
  FOREIGN KEY (ClientID) REFERENCES Client(ClientID)
);

CREATE TABLE Client_Phone
(
  Phone varchar(20) NOT NULL,
  ClientID INT NOT NULL,
  PRIMARY KEY (Phone, ClientID),
  FOREIGN KEY (ClientID) REFERENCES Client(ClientID)
);

CREATE TABLE Salesperson_Phone
(
  Phone varchar(20) NOT NULL,
  SalespersonID INT NOT NULL,
  PRIMARY KEY (Phone, SalespersonID),
  FOREIGN KEY (SalespersonID) REFERENCES Salesperson(SalespersonID)
);

CREATE TABLE Car
(
  CarID INT NOT NULL,
  Model varchar(20) NOT NULL,
  Color varchar(20) NOT NULL,
  Capacity INT ,
  Quantity INT ,
  SaleiD INT ,
  PRIMARY KEY (CarID),
  FOREIGN KEY (SaleiD) REFERENCES Sale(SaleiD)
);

CREATE TABLE Car_Features
(
  Features INT NOT NULL,
  CarID INT NOT NULL,
  PRIMARY KEY (Features, CarID),
  FOREIGN KEY (CarID) REFERENCES Car(CarID)
);

-- Insert dummy data into Client table
INSERT INTO Client (ClientID, Fname, Lname, Email, Street, City) VALUES
(1, 'John', 'Doe', 'johndoe@example.com', '123 Elm St', 'Springfield'),
(2, 'Jane', 'Smith', 'janesmith@example.com', '456 Oak St', 'Shelbyville'),
(3, 'Robert', 'Johnson', 'robertjohnson@example.com', '789 Pine St', 'Capitol City'),
(4, 'Emily', 'Davis', 'emilydavis@example.com', '321 Maple St', 'Springfield'),
(5, 'Michael', 'Brown', 'michaelbrown@example.com', '654 Cedar St', 'Shelbyville'),
(6, 'Sarah', 'Wilson', 'sarahwilson@example.com', '987 Birch St', 'Capitol City'),
(7, 'David', 'Taylor', 'davidtaylor@example.com', '111 Oak St', 'Springfield'),
(8, 'Laura', 'Anderson', 'lauraanderson@example.com', '222 Pine St', 'Shelbyville'),
(9, 'James', 'Thomas', 'jamesthomas@example.com', '333 Maple St', 'Capitol City'),
(10, 'Linda', 'Martinez', 'lindamartinez@example.com', '444 Cedar St', 'Springfield');
------------------------------------------------------------------------------------
-- Insert dummy data into Salesperson table
INSERT INTO Salesperson (SalespersonID, Fname, Lname, Email, Work_hours) VALUES
(1, 'Alice', 'Brown', 'alicebrown@example.com', 40),
(2, 'Charlie', 'Davis', 'charliedavis@example.com', 35),
(3, 'Eve', 'Miller', 'evemiller@example.com', 30),
(4, 'Frank', 'Wilson', 'frankwilson@example.com', 45),
(5, 'Grace', 'Moore', 'gracemoore@example.com', 25),
(6, 'Henry', 'Taylor', 'henrytaylor@example.com', 50),
(7, 'Ivy', 'Anderson', 'ivyanderson@example.com', 20),
(8, 'Jack', 'Thomas', 'jackthomas@example.com', 35),
(9, 'Kate', 'Martinez', 'katemartinez@example.com', 40),
(10, 'Leo', 'Martin', 'leomartin@example.com', 30);
------------------------------------------------------------------
-- Insert dummy data into Sale table
INSERT INTO Sale (SaleID, Date, Price, PaymentMethod, AdditionalFees, SalespersonID, ClientID) VALUES
(1, '2023-01-15', 25000.00, 'Credit Card', 500.00, 1, 1),
(2, '2023-02-20', 30000.00, 'Cash', 0.00, 2, 2),
(3, '2023-03-10', 22000.00, 'Credit Card', 300.00, 3, 3),
(4, '2023-04-05', 28000.00, 'Cash', 200.00, 4, 4),
(5, '2023-05-20', 31000.00, 'Credit Card', 400.00, 5, 5),
(6, '2023-06-15', 27000.00, 'Cash', 0.00, 6, 6),
(7, '2023-07-10', 29000.00, 'Credit Card', 100.00, 7, 7),
(8, '2023-08-25', 26000.00, 'Cash', 150.00, 8, 8),
(9, '2023-09-15', 32000.00, 'Credit Card', 300.00, 9, 9),
(10, '2023-10-05', 24000.00, 'Cash', 50.00, 10, 10);
-----------------------------------------------------------
-- Insert dummy data into Client_Phone table
INSERT INTO Client_Phone (Phone, ClientID) VALUES
('555-1234', 1),
('555-5678', 2),
('555-8765', 3),
('555-2345', 4),
('555-6789', 5),
('555-9876', 6),
('555-3456', 7),
('555-7890', 8),
('555-0987', 9),
('555-6543', 10);
--------------------------------------------------------------
-- Insert dummy data into Salesperson_Phone table
INSERT INTO Salesperson_Phone (Phone, SalespersonID) VALUES
('555-4321', 1),
('555-8765', 2),
('555-7654', 3),
('555-5432', 4),
('555-6543', 5),
('555-9876', 6),
('555-6789', 7),
('555-0987', 8),
('555-3456', 9),
('555-4567', 10);
-----------------------------------------------------------

-- Insert dummy data into Car table
INSERT INTO Car (CarID, Model, Color, Capacity, Quantity, SaleID) VALUES
(1, 'Sedan', 'Red', 5, 10, 1),
(2, 'SUV', 'Blue', 7, 5, 2),
(3, 'Coupe', 'Black', 4, 3, 3),
(4, 'Convertible', 'Yellow', 2, 4, 4),
(5, 'Hatchback', 'Green', 5, 7, 5),
(6, 'Pickup', 'White', 3, 8, 6),
(7, 'Minivan', 'Gray', 7, 2, 7),
(8, 'Sedan', 'Blue', 5, 6, 8),
(9, 'SUV', 'Red', 7, 3, 9),
(10, 'Coupe', 'Black', 4, 5, 10);
-----------------------------------------------------------
-- Insert dummy data into Car_Features table
INSERT INTO Car_Features (Features, CarID) VALUES
(1, 1),
(2, 1),
(3, 2),
(4, 2),
(5, 3),
(6, 3),
(7, 4),
(8, 4),
(9, 5),
(10, 5);


-----------------------------------------------
```


## second :

restore `CarDB_Backup`

it is the initial database but after updating

which filled with data in csv file and mock data:

`python code for filling the data on carprice table:`

![1](../DATABASEPROJECT/pics/csv.png)

`the dummy data:`
``` sql
-- Inserting data into Branch table
INSERT INTO Branch (BranchID, BranchName, City) VALUES
('B001', 'Main Branch', 'Talkha'),
('B002', 'Mit Ghamr Branch', 'Mit Ghamr'),
('B003', 'Belqas Branch', 'Belqas'),
('B004', 'Aga Branch', 'Aga'),
('B005', 'Al Mahalla Al Kubra Branch', 'Al Mahalla Al Kubra')

-- Inserting data into Salesperson table
INSERT INTO Salesperson (SalespersonID, Fname, Lname, Email, Work_hours, BranchID) VALUES
('S001', 'David', 'Miller', 'david.m@example.com', 40, 'B001'),
('S002', 'Emma', 'Davis', 'emma.d@example.com', 35, 'B002'),
('S003', 'Olivia', 'Garcia', 'olivia.g@example.com', 30, 'B003'),
('S004', 'Liam', 'Martinez', 'liam.m@example.com', 45, 'B004'),
('S005', 'Sophia', 'Hernandez', 'sophia.h@example.com', 40, 'B005'),
('S006', 'James', 'Lopez', 'james.l@example.com', 50, 'B001'),
('S007', 'Isabella', 'Gonzalez', 'isabella.g@example.com', 30, 'B002'),
('S008', 'Benjamin', 'Wilson', 'benjamin.w@example.com', 35, 'B003'),
('S009', 'Charlotte', 'Anderson', 'charlotte.a@example.com', 40, 'B004'),
('S010', 'Michael', 'Thomas', 'michael.t@example.com', 45, 'B005');

-- Inserting data into Client table
INSERT INTO Client (ClientID, Fname, Lname, Email, Street, City) VALUES
('C001', 'John', 'Doe', 'john.doe@example.com', '123 Elm St', 'Talkha'),
('C002', 'Jane', 'Smith', 'jane.smith@example.com', '456 Oak St', 'Mit Ghamr'),
('C003', 'Alice', 'Johnson', 'alice.j@example.com', '789 Pine St', 'Belqas'),
('C004', 'Bob', 'Brown', 'bob.b@example.com', '101 Maple St', 'Aga'),
('C005', 'Charlie', 'Davis', 'charlie.d@example.com', '202 Birch St', 'Al Mahalla Al Kubra'),
('C006', 'Eve', 'Wilson', 'eve.w@example.com', '303 Cedar St', 'Talkha'),
('C007', 'Frank', 'Clark', 'frank.c@example.com', '404 Ash St', 'Mit Ghamr'),
('C008', 'Grace', 'Lewis', 'grace.l@example.com', '505 Spruce St', 'Belqas'),
('C009', 'Hank', 'Walker', 'hank.w@example.com', '606 Fir St', 'Aga'),
('C010', 'Ivy', 'Hall', 'ivy.h@example.com', '707 Palm St', 'Al Mahalla Al Kubra');

-- Inserting data into Sale table with the specified sequence
INSERT INTO Sale (SaleID, Date, Price, paymentMethod, AdditionalFees, Deposit, SalespersonID, ClientID, Rest, MonthlyPay) VALUES
('SA001', '2023-01-15', 21000, 'Credit Card', 500, 5000, 'S001', 'C001', 16000, 1333.33),
('SA002', '2023-01-20', 26000, 'Bank Transfer', 600, 6000, 'S002', 'C002', 20000, 1666.67),
('SA003', '2023-01-25', 31000, 'Cash', 700, 7000, 'S003', 'C003', 24000, 2000.00),
('SA004', '2023-02-01', 36000, 'Credit Card', 800, 8000, 'S004', 'C004', 28000, 2333.33),
('SA005', '2023-02-05', 41000, 'Bank Transfer', 900, 9000, 'S005', 'C005', 32000, 2666.67),
('SA006', '2023-02-10', 46000, 'Cash', 1000, 10000, 'S006', 'C006', 36000, 3000.00),
('SA007', '2023-02-15', 51000, 'Credit Card', 1100, 11000, 'S007', 'C007', 40000, 3333.33),
('SA008', '2023-02-20', 56000, 'Bank Transfer', 1200, 12000, 'S008', 'C008', 44000, 3666.67),
('SA009', '2023-02-25', 61000, 'Cash', 1300, 13000, 'S009', 'C009', 48000, 4000.00),
('SA010', '2023-03-01', 66000, 'Credit Card', 1400, 14000, 'S010', 'C010', 52000, 4333.33),
('SA011', '2023-03-05', 22000, 'Bank Transfer', 600, 6000, 'S001', 'C001', 16000, 1333.33),
('SA012', '2023-03-10', 27000, 'Cash', 700, 7000, 'S002', 'C002', 20000, 1666.67),
('SA013', '2023-03-15', 32000, 'Credit Card', 800, 8000, 'S003', 'C003', 24000, 2000.00),
('SA014', '2023-03-20', 37000, 'Bank Transfer', 900, 9000, 'S004', 'C004', 28000, 2333.33),
('SA015', '2023-03-25', 42000, 'Cash', 1000, 10000, 'S005', 'C005', 32000, 2666.67);



INSERT INTO match (id, saleid) VALUES
(1, 'SA001'),
(2, 'SA002'),
(3, 'SA003'),
(4, 'SA004'),
(5, 'SA005'),
(6, 'SA006'),
(7, 'SA007'),
(8, 'SA008'),
(9, 'SA009'),
(10, 'SA010'),
(11, 'SA011'),
(12, 'SA012'),
(13, 'SA013'),
(14, 'SA014'),
(15, 'SA015');



-- Inserting data into Car table with corresponding real car model names and manufacturers
INSERT INTO Car (CarID, Model, Color, Capacity, quantity, SaleiD, BranchID, Manufacturer) VALUES
('CAR001', 'Toyota Corolla', 'Red', 5, 10, 'SA001', 'B001', 'Toyota'),
('CAR002', 'Toyota Camry', 'Blue', 5, 10, 'SA002', 'B002', 'Toyota'),
('CAR003', 'Honda Civic', 'Green', 5, 10, 'SA003', 'B003', 'Honda'),
('CAR004', 'Honda Accord', 'Yellow', 5, 10, 'SA004', 'B004', 'Honda'),
('CAR005', 'Ford Focus', 'Black', 5, 10, 'SA005', 'B005', 'Ford'),
('CAR006', 'Ford Fusion', 'White', 5, 10, 'SA006', 'B001', 'Ford'),
('CAR007', 'Chevrolet Malibu', 'Gray', 5, 10, 'SA007', 'B002', 'Chevrolet'),
('CAR008', 'Chevrolet Impala', 'Pink', 5, 10, 'SA008', 'B003', 'Chevrolet'),
('CAR009', 'Nissan Altima', 'Purple', 5, 10, 'SA009', 'B004', 'Nissan'),
('CAR010', 'Nissan Maxima', 'Orange', 5, 10, 'SA010', 'B005', 'Nissan'),
('CAR011', 'Hyundai Elantra', 'Red', 5, 10, 'SA011', 'B001', 'Hyundai'),
('CAR012', 'Hyundai Sonata', 'Blue', 5, 10, 'SA012', 'B002', 'Hyundai'),
('CAR013', 'Volkswagen Jetta', 'Green', 5, 10, 'SA013', 'B003', 'Volkswagen'),
('CAR014', 'Volkswagen Passat', 'Yellow', 5, 10, 'SA014', 'B004', 'Volkswagen'),
('CAR015', 'Subaru Impreza', 'Black', 5, 10, 'SA015', 'B005', 'Subaru');


-- Inserting data into Car_Features table with corresponding real car model names and features
INSERT INTO Car_Features (Features, CarID) VALUES
('Sunroof', 'CAR001'),
('Leather Seats', 'CAR002'),
('Bluetooth', 'CAR003'),
('Backup Camera', 'CAR004'),
('Navigation System', 'CAR005'),
('Heated Seats', 'CAR006'),
('Remote Start', 'CAR007'),
('Blind Spot Monitoring', 'CAR008'),
('Parking Sensors', 'CAR009'),
('Adaptive Cruise Control', 'CAR010'),
('Apple CarPlay', 'CAR011'),
('Android Auto', 'CAR012'),
('Keyless Entry', 'CAR013'),
('Lane Departure Warning', 'CAR014'),
('Automatic Emergency Braking', 'CAR015');



-- Inserting data into Client_Phone table
INSERT INTO Client_Phone (Phone, ClientID) VALUES
('0100000001', 'C001'),
('0100000002', 'C002'),
('0100000003', 'C003'),
('0100000004', 'C004'),
('0100000005', 'C005'),
('0100000006', 'C006'),
('0100000007', 'C007'),
('0100000008', 'C008'),
('0100000009', 'C009'),
('0100000010', 'C010');


-- Inserting data into Coupon table
INSERT INTO Coupon (CouponnNo, Discount, SaleiD) VALUES
(1001, 10, 'SA001'),
(1002, 15, 'SA002'),
(1003, 20, 'SA003'),
(1004, 25, 'SA004'),
(1005, 30, 'SA005'),
(1006, 35, 'SA006'),
(1007, 40, 'SA007'),
(1008, 45, 'SA008'),
(1009, 50, 'SA009'),
(1010, 55, 'SA010');




-- Inserting data into Salesperson_Phone table
INSERT INTO Salesperson_Phone (Phone, SalespersonID) VALUES
('0200000001', 'S001'),
('0200000002', 'S002'),
('0200000003', 'S003'),
('0200000004', 'S004'),
('0200000005', 'S005'),
('0200000006', 'S006'),
('0200000007', 'S007'),
('0200000008', 'S008'),
('0200000009', 'S009'),
('0200000010', 'S010');


-- Inserting data into Shareholder table
INSERT INTO Shareholder (ShareholderID, Name, Percentage) VALUES
('SH001', 'Mr. Abdelfattah', 43.56),
('SH002', 'Mr. Madboli', 19.34),
('SH003', 'Mr. McMan', 37.10);
```
## finally :
after restoring the database you can understand the design , chech  relations , relationships, and queries .
