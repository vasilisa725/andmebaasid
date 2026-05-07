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
