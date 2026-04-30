## Andmebaas Hotelliruumi reserveerimine
```
--1. guest

CREATE TABLE guest(
guestID int Primary key identity(1,1),
firstname varchar(80),
lastname varchar(80) not null,
memberSince DATE);

SELECT * FROM guest;

INSERT INTO guest
VALUES ('vasilisa', 'vasilenko', '2026-04-30');
```
<img width="291" height="81" alt="{D046B9C3-4B39-46A1-96F3-89F37F637945}" src="https://github.com/user-attachments/assets/4ef0b6dd-2f63-4893-bd0d-f265528e9015" />

```
--2. reservation

CREATE TABLE reservation(
reservationID int PRIMARY KEY identity(1,1),
date_in DATE,
date_out DATE,
made_by varchar(20),
guestID int,
FOREIGN KEY (guestID) REFERENCES guest(guestID));

SELECT * FROM reservation;

INSERT INTO reservation
VALUES ('2026-01-12','2026-11-05','admin', 3);
```
<img width="365" height="78" alt="{D358D900-5AC6-4B4A-BF5A-75C3E2EA0702}" src="https://github.com/user-attachments/assets/8b7f2402-a399-4ffd-8fc8-199a8fc937c0" />


```
--3. room_type

CREATE TABLE room_type(
room_type_id int primary key identity(1,1),
descriprion varchar(80),
max_capacity int);

SELECT * FROM room_type;

INSERT INTO room_type
VALUES ('luks', 4);
```
<img width="263" height="76" alt="{4DDEFAC4-8984-452F-85DE-E5007A4EEF5F}" src="https://github.com/user-attachments/assets/7d1b48e9-1d9f-4ece-86e1-a1a812bcef08" />


```
--4. room

CREATE TABLE room(
room_id int primary key identity(1,1),
number varchar(10),
name varchar(40),
status varchar(10),
smoke bit,
room_type_id int,
foreign key (room_type_id) references room_type(room_type_id));

SELECT * FROM room;

INSERT INTO room
VALUES ('3', 'room3', 'reserved', 1,3);
```
<img width="367" height="76" alt="{FFC35378-47CF-42F7-AEFA-001C5F14CD31}" src="https://github.com/user-attachments/assets/d57e3723-be95-418a-a85e-910a3efff9c7" />


```

--5. reserved_room
CREATE TABLE reserved_room(
reserved_roomID int PRIMARY KEY identity(1,1),
number_of_rooms int,
room_typeID int,
reservationID int,
FOREIGN KEY (room_typeID) REFERENCES room_type(room_type_id),
FOREIGN KEY (reservationID) REFERENCES reservation(reservationID),
status varchar(20));
 

SELECT * FROM reserved_room;

INSERT INTO reserved_room
VALUES (2,3,1, 'ready');
```
<img width="429" height="78" alt="{13146C88-9BD4-408F-914F-60C925957869}" src="https://github.com/user-attachments/assets/06bee5e3-15e2-4819-9489-650c14adec31" />


```
CREATE TABLE occupied_room(
occupied_roomID int PRIMARY KEY identity(1,1),
check_in DATE,
check_out DATE,
roomID int,
reservationID int,
FOREIGN KEY (roomID) REFERENCES room(room_ID),
FOREIGN KEY (reservationID) REFERENCES reservation(reservationID));

SELECT * FROM occupied_room;

INSERT INTO reserved_room
VALUES ('2004-07-04', '2007-09-03', 1,1);
```
<img width="404" height="77" alt="{F82ADCDF-E150-411E-8B45-8920D473F64C}" src="https://github.com/user-attachments/assets/059e70c7-9f39-4c24-b40f-6b8a914385a6" />


```
CREATE TABLE hosted_room(
hosted_atID int PRIMARY KEY identity(1,1),
guest_id int,
occupied_room_id int,
FOREIGN KEY (guest_id) REFERENCES guest(guestID),
FOREIGN KEY (occupied_room_id) REFERENCES occupied_room(occupied_roomID));

SELECT * FROM hosted_room;

INSERT INTO hosted_room
VALUES (3,2);
```
<img width="260" height="75" alt="{F78CA3D2-B78D-4F20-9676-32297F6E5159}" src="https://github.com/user-attachments/assets/8405a152-894a-4489-9583-cc5f456da1a6" />

<img width="961" height="827" alt="{58D375DB-5C0D-4451-A028-FADEB521E1C2}" src="https://github.com/user-attachments/assets/0be13879-9cd2-4bd4-92fa-526f9a45dfcd" />

