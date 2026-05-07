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
