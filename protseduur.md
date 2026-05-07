## SQL Protseduurid
- store procedure - salvestatud protseduurid - хранимые процедуры
- sama nagu funktsioonid programmeerimises - mingi tehevused mis käivitakse automaatselt protseduuri kasutamisel

```
CREATE PROCEDURE lisaGuest
--@parameetrid 
@ussNimi varchar(25),
@uusPerenimi varchar(30),
@kuupaev date
AS
BEGIN
--protseduuri
INSERT INTO guest(firstname, lastname, memberSince)
VALUES (@ussNimi, @uusPerenimi, @kuupaev);
SELECT * FROM guest;
END
```
<img width="188" height="148" alt="{7C474409-51D0-41CE-BA74-35CEDECD6F20}" src="https://github.com/user-attachments/assets/9cb1f1bc-516d-46eb-aa09-6f2124fce562" />
<img width="482" height="185" alt="{315A47B6-93FF-4117-830E-F5AB02AF2207}" src="https://github.com/user-attachments/assets/535d64c8-f6cc-4215-8290-a5245dac14c5" />
<img width="448" height="676" alt="{6A50952C-F894-4F36-BC55-2B08696690E0}" src="https://github.com/user-attachments/assets/2969ac0b-2cc1-4a25-89ce-f44d4ace0e19" />

```
EXEC kustutaGuest 1;

--otsing esimese tähe järgi
CREATE PROCEDURE otsing1taht
@taht char(1)
AS
BEGIN
 SELECT * FROM guest WHERE firstname LIKE @taht + '%';
END

EXEC otsing1taht 'L'
```
