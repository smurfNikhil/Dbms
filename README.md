# Dbms
The Hospital Management System is a DBMS-based project designed to streamline the administrative and operational functions of a hospital. It provides an efficient way to manage patient records, doctor schedules, appointments, billing, and other hospital-related information.
The system uses a relational database management system (RDBMS) to store and manage data securely and efficiently. The goal is to reduce manual workload, minimize errors, and provide quick access to critical information.
Create Database Nikhil;
Use Nikhil;
create table Patients(
Patient_ID int primary key,
P_Name char(30),
P_Age int,
Gender char(20),
P_ContactNo int,
P_Address varchar(50),
BloodType varchar(10),
AdmissionDate date,
DischargeDate date
);

Describe Patients;

create table Doctors(
Doctor_ID int primary key,
D_Name char(30),
Specialization char(20),
D_ContactNo int,
Email_ID varchar(20),
DepartmentID int
);

Describe Doctors;

create table Department(
DepartmentID int primary key,
Dep_Name char(30),
Location varchar(20)
);

Describe Department;

alter table Doctors
Add foreign key(DepartmentID)
references Department(DepartmentID);

create table Appointments(
AppointmentID int primary key,
Patient_ID int,
Doctor_ID int,
AppointmentDate date,
A_status char(20)
);

alter table Appointments
add foreign key (Patient_ID)
references Patients(Patient_ID);

alter table Appointments
add foreign key (Doctor_ID)
references Doctors(Doctor_ID);

describe Appointments;

create table Medical_Records(
Record_ID int primary key,
Patient_ID int,
Diagnosis char(20),
Treatment char(20),
PrescribedMedicine char(20),
Doctor_ID int,
DateOfEntry date
);

alter table Medical_Records
add foreign key (Patient_ID)
references Patients(Patient_ID);

alter table Medical_Records
add foreign key (Doctor_ID)
references Doctors(Doctor_ID);

Describe Medical_Records;

create table Billing(
Bill_ID int primary key,
Patient_ID int,
TotalAmount int,
PaymentStatus char(20),
DateIssued date
);

alter table Billing
add foreign key (Patient_ID)
references Patients(Patient_ID);

describe Billing;

create table Pharmacy(
Med_ID int primary key,
Med_Name char(20),
StockQuantity int,
Price int
);

describe Pharmacy;

create table Staff(
S_ID int primary key,
S_Name char(40),
S_Role char(30),
S_ContactNo int,
S_Department int
);

describe Staff;

alter table Staff
add foreign key(S_Department)
references Department(DepartmentID);

select*from Staff;

insert into Patients(Patient_ID,P_Name,P_Age,Gender,P_ContactNo,P_Address,BloodType,AdmissionDate,DischargeDate)
values
(101,'Rahul Sharma',45,'Male',9945783,'Delhi,India','B+','2024-02-10','2024-02-15'),
(102,'Priya Verma',30,'Female',896005,'Mumbai,India','O+','2024-03-05',NULL),
(103,'Amit Singh',55,'Male',781432,'Kolkata,India','A-','2024-01-20','2024-02-01'),
(104,'Sneha Kapoor',28,'Female',620043,'Bangalore,India','AB+','2024-02-22','2024-02-28'),
(105,'Rohit Mehta',33,'Male',907611,'Chennai,India','O-','2024-03-10',NULL),
(106,'Neha Joshi',40,'Female',994310,'Pune,India','B-','2024-01-15','2024-01-30'),
(107,'Varun Malhotra',29,'Male',879901,'Hyderabad,India','A+','2024-02-05','2024-02-12'),
(108,'Ananya Sen',35,'Female',624821,'Jaipur,India','AB-','2024-03-02',NULL);

select*from Patients;

insert into Doctors(Doctor_ID,D_Name,Specialization,D_ContactNo,Email_ID,DepartmentID)
values
(201,'Dr.Arjun Rao','Cardiology',985621,'Arjun01@hospital.com',1),
(202,'Dr.Meera Das','Neurology',870023,'Meera02@hospital.com',2),
(203,'Dr.Karan Jain','Orthopedics',992567,'Karan03@hospital.com',3),
(204,'Dr.Aditi Roy','Dermatology',790112,'Aditi04@hospital.com',4),
(205,'Dr.Ravi Gupta','Pediatrics',975344,'Ravi05@hospital.com',5),
(206,'Dr.Sonia Kapoor','Gynecology',885132,'Sonia06@hospital.com',6),
(207,'Dr.Aman Khanna','ENT',799203,'Aman07@hospital.com',7),
(208,'Dr.Pooja Mehta','General Medicine',992116,'Pooja08@hospital.com',8);

select*from Doctors;

insert into Department(DepartmentID,Dep_Name,Location)
values
(1,'Cardiology','Block A-1st Floor'),
(2,'Neurology','Block B-2nd Floor'),
(3,'Orthopedics','Block C-3rd Floor'),
(4,'Dermatology','Block D-4th Floor'),
(5,'Pediatrics','Block E-5th Floor'),
(6,'Gynecology','Block F-6th Floor'),
(7,'ENT','Block G-7th Floor'),
(8,'General Medicine','Block H-Ground Floor');

select*from Department;

insert into Appointments(AppointmentID,Patient_ID,Doctor_ID,AppointmentDate,A_Status)
values
(301,101,201,'2024-02-11','Completed'),
(302,102,202,'2024-03-06','Scheduled'),
(303,103,203,'2024-01-21','Completed'),
(304,104,204,'2024-02-23','Completed'),
(305,105,205,'2024-03-11','Scheduled'),
(306,106,206,'2024-01-16','Completed'),
(307,107,207,'2024-02-06','Completed'),
(308,108,208,'2024-03-03','Scheduled');

select*from Appointments;

insert into Medical_Records(Record_ID,Patient_ID,Diagnosis,Treatment,PrescribedMedicine,Doctor_ID ,DateOfEntry)
values
(4001,101,'Hypertension','Medication','Amlodipine',201,'2024-02-11'),
(4002,102,'Migraine','Therapy','Sumatriptan',202,'2024-03-06'),
(4003,103,'Fracture','Surgery','Painkillers',203,'2024-01-21'),
(4004,104,'Skin Allergy','Ointment','Hydrocortisone',204,'2024-02-23'),
(4005,105,'Fever','Rest & Fluids','Paracetamol',205,'2024-03-11'),
(4006,106,'Pregnancy Check','Monitoring','Vitamins',206,'2024-01-16'),
(4007,107,'Ear Infection','Antibiotics','Amoxicillin',207,'2024-02-06'),
(4008,108,'Diabetes','MDiet Control','Insulin',208,'2024-03-03');

select*from Medical_Records;

insert into Billing(Bill_ID,Patient_ID,TotalAmount,PaymentStatus,DateIssued)
values
(5000,101,5000,'Paid','2024-02-15'),
(50002,102,3000,'Pending','2024-03-06'),
(5003,103,15000,'Paid','2024-01-21'),
(5004,104,7000,'Paid','2024-02-23'),
(5005,105,2500,'Pending','2024-03-11'),
(5006,106,4000,'Paid','2024-01-16'),
(5007,107,6000,'Paid','2024-02-06'),
(5008,108,9000,'Pending','2024-03-03');

select*from Billing;

insert into Pharmacy(Med_ID,Med_Name,StockQuantity,Price)
values
(6001,'Paracetamol',100,10),
(6002,'Amoxicillin',50,20),
(6003,'Amlodipine',80,15),
(6004,'Insulin',30,50),
(6005,'Sumatriptan',20,40),
(6006,'Hydrocortisone',25,25),
(6007,'Painkillers',60,12),
(6008,'Vitamins',90,30);

select*from Pharmacy;

insert into Staff(S_ID,S_Name ,S_Role,S_ContactNo,S_Department)
values
(7001,'Sunita Sharma','Nurse',991462,1),
(7002,'Ramesh Gupta','Receptionist',98743,8),
(7003,'Anjali Verma','Lab Technician',80032,2),
(7004,'Suresh Mehta','Pharmacist',781400,8),
(7005,'SPoonam Kaur','Ward Boy',894211,3),
(7006,'Kavita Joshi','Nurse',774112,5),
(7007,'Mohit Bansal','Cleaner',993899,6),
(7008,'SDeepa Rani','Accountant',98148,8);

select*from Staff;

select*from Patients;

select doctors.D_Name,Department.Dep_Name
from Doctors
inner join Department on Doctors.DepartmentID=Department.DepartmentID;

select*from Appointments
where AppointmentDate>'2024-03-01';

select Patients.P_Name,Medical_Records.Diagnosis,Medical_Records.PrescribedMedicine
from Medical_Records
inner join Patients on Patients.Patient_ID=Medical_Records.Patient_ID;

select sum(TotalAmount) as TotalPaidAmount
from Billing
where PaymentStatus='Paid';

select Staff.S_Name,Staff.S_Role,Department.Dep_Name
from Staff
join Department on Staff.S_Department=Department.DepartmentID
where Department.Dep_Name='General Medicine';

select*from Pharmacy
where StockQuantity<30;

update Billing
Set PaymentStatus='Paid'
where Bill_ID=502;

SELECT P_Age, COUNT(*) AS PatientCount
FROM Patients
GROUP BY P_Age
HAVING COUNT(*) <2;

SELECT P_Name, AdmissionDate,
COUNT(*) OVER () AS FebAdmissions
FROM Patients
WHERE MONTH(AdmissionDate) = 2 AND YEAR(AdmissionDate) = 2024;

Select Doctors.D_Name,Doctors.Specialization,Department.Location
from Doctors
join Department on Department.DepartmentID=Doctors.DepartmentID
where Department.Location Like '%1st Floor%' OR Department.Location Like '%2nd Floor%';

select Patients.P_Name,Billing.TotalAmount
from Billing
join Patients on Billing.Patient_ID=Patients.Patient_ID
Order BY Billing.TotalAmount;

select Patients.P_Name,Billing.TotalAmount
from Billing
join Patients on Billing.Patient_ID=Patients.Patient_ID
Order BY Billing.TotalAmount desc
Limit 1;
