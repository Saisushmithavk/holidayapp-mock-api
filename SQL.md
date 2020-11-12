//Task #1: Create Database

create database holidayapp_db;
use holidayapp_db;

//Task 2: Create registration table

create table registration(
id int primary key auto_increment,
name varchar(30) not null,
email varchar(20) not null,
password varchar(15) not null,
role varchar(10) not null,
unique(email),
check (role in ('USER','ADMIN'))
​
);
​
//Task 2.1: create value to registration
​
insert into registration(name,email,password,role) values('nithisha','nithisha@123gmail.com','nithisha123','USER');
​
insert into registration(name,email,password,role) values('rohit','rohith@123gmail.com','rohit@13','USER');
​
insert into registration(name,email,password,role) values('sai','sai@123gmail.com','sai@1111','ADMIN');

//Task 2.2: List all registration

select * from registration;

// Task 2.3: create signin Table

create table signin(
id int primary key auto_increment,
user_id int not null,
email varchar(20) not null,
password varchar(15) not null,
foreign key (user_id) references registration(id)
​
);
​
//inserting into signin table
​
insert into signin (email,password,role) values ('sai@gmail.com','sai@111','ADMIN');

update signin set active =1 where id = 1;

//Task 3: Create destination table

create table destination
(
dest_id int primary key auto_increment,
destname varchar(30),
description text(500),
priority varchar(50),
status varchar(50));

//Task 3.1: update destination
insert int
insert into destination (destname, description) values ('DUMAS BEACH-Gujarat','considered one of the most haunted places in Gujarat.');
insert into destination (destname, description) values ('AGONDA BEACH-goa','serves as a nesting ground for olive ridley sea turtles.');


//Task 3.2: list Destination

select * from destination where destname='DUMAS BEACH-Gujarat';

//Task 4: create Packages

create table packages 
( 
dest_id int primary key auto_increment,
user_id int not null,
packagename varchar(50) not null,
price int,
duration int,
active boolean not null default 0,
unique ( user_id, packagename),
foreign key (user_id) references destination(dest_id));

//Task 4.1: insert values to packages

insert into packages (user_id,packagename,price,duration) values (1,'DUMAS-GUJARAT',20000,3);
insert into packages (user_id,packagename,price,duration) values (2,'AGONDA-GOA',23000,2);

//Task: 4.2 list packages to user

select * from packages where packagename='DUMAS-GUJARAT';

//Task 5: Book Package
create table bookpackage(
user_id int primary key auto_increment,
book_id int not null,
packagename varchar(50) not null,
price int,
duration int,
facilities varchar(40),
active boolean not null default 0,
unique ( book_id, packagename),
foreign key (book_id) references packages(user_id));

//TASK 5.1: insert table to bookpackage

insert into bookpackage(book_id,packagename,price,duration,facilities) values(1,'DUMAS-GUJARAT','20000',3,'ac,pool,lodging');
insert into bookpackage(book_id,packagename,price,duration,facilities) values(2,'AGONDA-GUJARAT','20000',3,'ac,pool,lodging');

//Task: 5.2 View Bookings

select * from bookpackage where book_id=2;
