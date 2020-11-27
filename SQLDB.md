# Holidayapp-db-SQL

#### Task #1: Create Database
```
create database holiday_app;
use holiday_app;

```
#### Task 2: Create users table
```
create table users(
id int primary key auto_increment,
name varchar(30) not null,
email varchar(40) not null,
password varchar(15) not null,
role varchar(10) not null);

```

#### Task 2.1: insert values to users
```
insert into users(name,email,password,role) values('nithisha','nithisha@123gmail.com','nithisha123','USER');
insert into users(name,email,password,role) values('admin','admin@gmail.com','admin#123','ADMIN');
```
#### Task 2.2: List all users
```
select * from users;
```

#### Task 2.3: create destination Table
```
create table destination(
id varchar(15),
title varchar(30),
description text(1000));
``` 

#### Task 2.4: insert values into destination table
```
insert into destination(id,title,description) values("gujarat","Dumash Beach", "Located along the Arabian Sea, Dumas Beach is considered one of the most haunted places in Gujarat. The beach is renowned for two things, one for its black sand and other for being haunted!");
insert into destination(id,title,description) values("goa","Agonda Beach", "Agonda Beach is a public beach located in Agonda village in Goa, India, about 9.2 kilometres (5.7 mi) north of Palolem Beach in South Goa district, and about an hour from Margao During the month of September, the beach serves as a nesting ground for olive ridley sea turtles.");
insert into destination(id,title,description) values("thanjavur","Brihadeeshwara Temple", "Brihadishvara Temple, also called Rajarajesvaram or Peruvudaiyār Kōvil, is a Hindu temple dedicated to Shiva located in South bank of Kaveri river in Thanjavur, Tamil Nadu, India.It is one of the largest South Indian temples and an exemplary example of a fully realized Dravidian architecture.");
```
### Task 2.5: List destination list
```
selelct * from destination;
```
#### Task 3: Create packages table
```
create table packages(
id int primary key not null,
Duration int not null,
Ratings int not null,
Facilities varchar(50),
Price int not null);
```
#### Task 3.1: insert values to packages
```
insert into packages(id,Duration,Ratings,Facilities,Price) values(101,3,4,"pool, gym,Hotel",24000);
insert into packages(id,Duration,Ratings,Facilities,Price) values(102,4,3,"gym,Hotel",20000);
insert into packages(id,Duration,Ratings,Facilities,Price) values(103,4,3,"gym,Hotel",20000);
```
#### Task 3.2: list packages
```
select * from packages;

```
### Task 4: create viewdestination
```
create table viewdestination(
id varchar(15),
destitle varchar(30),
descr text(1000));
```
### Task 4.1: insert values to view destination
```
insert into viewdestination (id,destitle,descr) values("gujarat","DUMAS BEACH-GUJARAT","Dumas Beach is an urban beach along the Arabian Sea, located 21 kilometres 13 mi southwest of the City of Surat in the Indian state of Gujarat.It is a popular tourist destination in South Gujarat. Dumas Beach is unjustly infamous for being in the top 35 haunted spots in India");
insert into viewdestination (id,destitle,descr) values("goa","AGONDA BEACH-GOA","Agonda is a large village located in Canacona in South Goa district, India. Agonda is famous for its beach and It is one of the only four beaches designated as turtle nesting sites under the Coastal Regulation Zone 2011 notification.There is one more beach on other side of Agonda cliff called Cola beach which has an adjoining lagoon.");
insert into viewdestination (id,destitle,descr) values("Thanjavur","BRIHADESHWARA TEMPLE-TANJAVUR","Brihadishvara Temple, also called Rajarajesvaram or Peruvudaiyar Kovil, is a Hindu temple dedicated to Shiva located in South bank of Kaveri river in Thanjavur, Tamil Nadu, India.It is one of the largest South Indian temples and an exemplary example of a fully realized Dravidian architecture.
 It is called as Dhakshina Meru (Meru of south).Built by Tamil king Raja Raja Chola I between 1003 and 1010 AD, the temple is a part of the UNESCO World Heritage Site known as the Great Living Chola Temples, along with the Chola dynasty era Gangaikonda Cholapuram temple and Airavatesvara temple that are about 70 kilometres (43 mi) and 40 kilometres (25 mi) to its northeast respectively.");
insert into viewdestination (id,destitle,descr) values("jaipur","HAWAMAHAL-JAIPUR","Hawa Mahal (English translation: The Palace of Winds or The Palace of Breeze is a palace in Jaipur, India approximately 300 kilometers from the capital city of Delhi. Built from red and pink sandstone, the palace sits on the edge of the City Palace,Jaipur, and extends to the Zenana, or women's chambers.
 The structure was built in 1799 by Maharaja Sawai Pratap Singh, the grandson of Maharaja Sawai Jai Singh, who was the founder of Jaipur. He was so inspired by the unique structure of Khetri Mahal that he built this grand and historical palace. It was designed by Lal Chand Ustad. Its five floor exterior is akin to honeycomb with its 953 small windows called Jharokhas decorated with intricate latticework.");
```
### Task: 4.2 list viewdestinations list
```
select * from viewdestination;

```
### Task 5: create bookings
```
create table bookings(
id int primary key auto_increment,
user_id int not null,
pack_id int not null,
status varchar(15) default 'BOOKED',
start_date date not null,
end_date date not null,
created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP ,
modified_date DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP  
);
```
### TASK 5.1: insert into to bookings
```
insert into bookings(user_id,pack_id,start_date,end_date) values(122,1,now(),now());

```
### Task: 5.2 View Bookings
```
SELECT b.*, p.Ratings,p.Duration,p.price,p.Facilities,u.name from bookings b, packages p, users u where b.pack_id = p.id and b.user_id = u.id;

```
