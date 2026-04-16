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
    ```
    
  - Admete sisetamine tabelisse
    ```
    ```
