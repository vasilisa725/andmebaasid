## Trigger - triger -päästik

- andmebaasi objekt, mis automaatsrlt käivitud tabeli sundmused (INSERT, UPDATE, DELETE)
## SQL
```
create database trigertitpv24;
USE trigertitpv24;
--

Create table linnad(
linnID int PRIMARY KEY IDENTITY (1,1),
linnanimi varchar(15) NOT NULL,
rahvaarv int);

--tabel, mis täidab triger 
Create table logi(
id int PRIMARY KEY IDENTITY (1,1),
kasutaja varchar(25),
aeg DATETIME,
toiming  varchar(100),
andmed TEXT --triger automaaselt lisab mida sekretaar lisas/kustutas  tabelisse linnad
)

select * from linnad;
select * from logi;
--Trigger lisatud kirjeid jälgimiseks tabelis “linnad” – INSERT
--Jälgib andmete sisestamine tabelis linnad ja teeb vastava kirje tabelis log


CREATE TRIGGER linnaLisamine
ON linnad --tabelinimi, mis on vaja jälgida
FOR INSERT
AS
INSERT INTO logi(kasutaja, aeg, toiming, andmed)
SELECT
SYSTEM_USER,
GETDATE(),  --aeg
'on tehtud INSERT käsk',  --toiming
inserted.linnanimi  --andmed
FROM inserted;


--kontrollimiseks insert into linnad
INSERT INTO linnad(linnanimi, rahvaarv)
VALUES ('Pärnu', 50000);
select * from linnad;
select * from logi;


--trigeri muutmine
ALTER TRIGGER linnaLisamine
ON linnad --tabelinimi, mis on vaja jälgida
FOR INSERT
AS
INSERT INTO logi(kasutaja, aeg, toiming, andmed)
SELECT
SYSTEM_USER,
GETDATE(),  --aeg
'on tehtud INSERT käsk',  --toiming
CONCAT ('linn:', inserted.linnanimi , ' rahvaarv: ' , inserted.rahvaarv) --andmed
FROM inserted;

--delete triger
CREATE TRIGGER linnaKustutamine
ON linnad --tabelinimi, mis on vaja jälgida
FOR INSERT
AS
INSERT INTO logi(kasutaja, aeg, toiming, andmed)
SELECT
SYSTEM_USER,
GETDATE(),  --aeg
'on tehtud DELETE käsk',  --toiming
CONCAT ('linn:', deleted.linnanimi , ' rahvaarv: ' , deleted.rahvaarv) --andmed
FROM deleted;

--kontroll--kustutada tabelist linnad
DELETE FROM linnad WHERE linnID=1;
select * from linnad;
select * from logi;

--update triger 
CREATE TRIGGER linnaUuendamine
ON linnad --tabelinimi, mis on vaja jälgida
FOR UPDATE
AS
INSERT INTO logi(kasutaja, aeg, toiming, andmed)
SELECT
SYSTEM_USER,
GETDATE(),  --aeg
'on tehtud UPDATE käsk',  --toiming
CONCAT ('VANAD: linn:', deleted.linnanimi , ' rahvaarv: ' , deleted.rahvaarv,
' ||| UUED: linn:', inserted.linnanimi , ' rahvaarv: ' , inserted.rahvaarv)
FROM deleted INNER JOIN inserted
ON deleted.linnID=inserted.linnID;

--kontrollimiseks tuleb 
UPDATE linnad SET linnanimi='Pärnu-väike', rahvaarv=50 WHERE linnID=1;
select * from linnad;
select * from logi;
```

<img width="921" height="565" alt="{D52A341C-1903-4B86-B104-4777E52E38C0}" src="https://github.com/user-attachments/assets/e8bc79b6-04d8-48c1-b142-5dd4496281d9" />


<img width="562" height="584" alt="{B2B9FC62-2766-4493-B7F8-76E433A0185C}" src="https://github.com/user-attachments/assets/67e78457-0c95-4d29-a840-7e34363a93dd" />


<img width="955" height="752" alt="{45E4A3DB-EE4B-4ECD-BFF9-DDF283D4FF93}" src="https://github.com/user-attachments/assets/10c9f5c7-5488-45d5-91a0-da05cc6e9b45" />


<img width="692" height="706" alt="{36EF01EE-C915-4D64-9737-F3EC42A1ED65}" src="https://github.com/user-attachments/assets/a4e13af1-8fa4-4641-8040-3275721ffb19" />


<img width="734" height="726" alt="{13B15604-DBE8-42F2-9290-5AB3DA5A9919}" src="https://github.com/user-attachments/assets/932e5920-697b-4337-84e4-df2cb7934247" />


## XAMPP

<img width="864" height="211" alt="{21F6198E-1DD8-408B-B6A7-35456D468C22}" src="https://github.com/user-attachments/assets/a1816e20-fc48-4d6d-b588-e6d2f929c0a6" />

