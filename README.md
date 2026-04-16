# Andmebaasid
andmebaasidega seotud SQL kood ja konspektid
## Põhimõisted
-
- andmebaas - struktureeritud admete kogum
- tabel = olem - сущность - entity
- veerg = väli - поле*столбец
- rida = kirje -записи
- admevaasi haildussüstem - tarkvara, millega abil saab luua andmebaas: mariaDB / XAMPP, SQL SERVER management Studio <img width="300" height="300" alt="{75CF2265-9EB7-43D8-89F7-6ED892CD35DC}" src="https://github.com/user-attachments/assets/2187035c-4c49-44b0-9aa2-8ea7c5a2ba00" />
- primaarne võti - PRIMARY KEY - veerg(tavaliselt id nimega), unikaalne identifikaator, mis eristab iga kirje.
- välisvõti - FOREIGN KEY -FK- veerg,mis loob seos teise tabeli primaarvõtmega.
- paring - QUERY - запрос

  ## Admetüübid
  ```
  1. Numbrilised: INT, SmallINT, float, decimal(5,2)
  2. Tekst/sümboolised: varchar(255), char(5), TEXT
  3. Loogilised: boolean, true/false, bit, bool
  4. Kuupäeva: date, time, datetime
  ```
  ## SQL - structure Query Language - struktureeritud päringu keel
  - Tabeli loomine
 ```
 CREATE TABLE opilane(
 opilaneID int Primary Key identity(1,1), --automaatselt täibsd numbri
 eesnimi varchar(25),
 perenimi varchar(30) NOT NULL,
 synniaeg DATE, 
 stip bit,
 mobiil varchar(13),
 aadress TEXT,
 keskmineHinne decimal(2,1) --(2--kokku, 1-peale komatnt 4.5)
 );
 SELECT * FROM opilane;
 --tabeli täitmine 
 INSERT INTO opilane
 VALUES ('Artjom', 'Jegorov', '2000-12-10',1, '+372848','Tallinn', 4.5);

 INSERT INTO opilane(perenimi, eesnimi, keskmineHinne)
 VALUES ('Merkulova', 'Irina', 4.2),
 ('Vasilenko', 'Vasilisa', 4.2),
 ('Talibova', 'Leyla', 4.2),
 ('Suvorov', 'Marko', 4.2);

 --andmete uue
 UPDATE opilane SET stip=1, aadress='Tallinn';

 UPDATE opilane SET stip=1, aadress='Tartu' WHERE opilaneID=5;
 DROP TABLE opilane;
 DELETE FROM opilane WHERE opilaneID=2;
 Select * from opilane;
```
    
  - Admete sisetamine tabelisse
    ```
    ```
    ## Seosed (tabelivahelised seosed)
    - ülk-ühele (nt mees-naine)
    - üks-mitmele (nt ema-lapsed)
    <img width="300" height="300" alt="{95A32110-C29B-4A97-92B8-81AA90C89945}" src="https://github.com/user-attachments/assets/ea44d13c-d0b6-41c8-973a-4bd06dcea69b" />
    - mitu-mitmele (nt õpilane - õpetajad)

      ## PIIRANGUD
      constraint - ограничения (5)
      1. PRIMARY KEY
      2. FOREIGN KEY
      3. CHECK
      4. NOT NULL
      5. UNIQUE

 ```
 CREATE TABLE opetamine(
 opetanineId int PRIMARY KEY identity(1,1),
 kuupaev DATE,
 oppeaine varchar(30),
 opilaneID int,
 FOREIGN KEY (opilaneID) REFERENCES opilane(opilaneID),
 hinne int CHECK(hinne<=5));

 SELECT * FROM opetamine;
 SELECT * FROM opilane;

 INSERT INTO opetamine
 VALUES ('2026-04-16', 'andmebaasid', 6, 4)
 ```




```
--õpetaja
CREATE TABLE opetaja(
opetajaID int Primary Key identity(1,1),
nimi varchar(25),
epost varchar(35),
ruhm  varchar(30) );
 
SELECT * FROM opetaja;
INSERT INTO opetaja
VALUES ('Anton', 'anton@gmail.com','TITpv24');

INSERT INTO opetaja (nimi, epost, ruhm)
VALUES ('Lury', 'lury@gmail.com', 'TITpv24'),
('Agapov', 'agapov@gmail.com','TITpv24');

--2
CREATE TABLE tund(
tundId int PRIMARY KEY identity(1,1),
kuupaev DATE,
tundnimi varchar(30),
opetajaID int,
FOREIGN KEY (opetajaID) REFERENCES opetaja(opetajaID),
opetamineID int,
FOREIGN KEY (opetamineID) REFERENCES opetaja(opetamineID)
);

SELECT * FROM tund;

INSERT INTO tund(kuupaev, tundnimi, opetajaID, opetamineID)
VALUES ('2026-04-16', 'Windows', 1,1),
('2026-04-17', 'Linux', 2,2),
('2026-04-18', 'Operatsioone', 3,3);
TRUNCATE TABLE tund;

DROP TABLE tund

```
