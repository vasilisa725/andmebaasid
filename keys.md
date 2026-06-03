## Andmebaasi võtmed (Keys)

[Põhimõsted](README.md) | [Protseduur](protseduur.md) | [Protseduur 14.05.2026](14.05.2026.md) | [GBS](gbs.md) | [Hotelliruum](hotelliruum.md) | [Keys](keys.md) | [Trigger](triger.md)

## Primary Key
1.Andmebaaside relatsioonimudelis on primaarvõti määratud atribuutide (veergude) kogum, mis suudab usaldusväärselt tuvastada ja eristada tabeli iga üksikut kirjet.
Andmebaasi looja saab valida tabelist olemasoleva unikaalse atribuudi või atribuutide kombinatsiooni (loomulik võti), mis toimib primaarvõtmena, või luua uue atribuudi, mis sisaldab unikaalset ID-d, mis eksisteerib ainult selleks otstarbeks (asendusvõti).

allikas: ```https://en.wikipedia.org/wiki/Primary_key```

<img width="351" height="245" alt="{6F336DD7-8BF3-4006-A3BB-315AD5783041}" src="https://github.com/user-attachments/assets/68a5c65c-c9a2-4dc0-9e64-f940a46844a6" />

## Foreign Key

2.Võõrvõti on tabeli atribuutide kogum, mis viitab teise tabeli primaarvõtmele, ühendades need kaks tabelit. 
Relatsioonandmebaaside kontekstis kehtib võõrvõtmele kaasamissõltuvuse piirang, mille kohaselt peavad ühe seose R võõrvõtme atribuutidest koosnevad tuupid eksisteerima ka mõnes teises (mitte tingimata erinevas) seoses S; lisaks peavad need atribuudid olema ka S-i võtme kandidaatideks.

allikas:```https://en.wikipedia.org/wiki/Foreign_key```

<img width="546" height="499" alt="{31401FE0-98D7-445D-BCD8-5F41470B8DEC}" src="https://github.com/user-attachments/assets/720f019e-4bc6-4a75-8520-e35ee9b79be2" />

## Unique Key
3.Relatsioonandmebaaside haldussüsteemides on unikaalne võti kandidaatvõti. 
Kõik relatsiooni kandidaatvõtmed saavad relatsiooni kirjeid unikaalselt identifitseerida, kuid ainult ühte neist kasutatakse relatsiooni primaarvõtmena. Ülejäänud kandidaatvõtmeid nimetatakse unikaalseteks võtmeteks, kuna need saavad relatsioonis kirje unikaalselt identifitseerida. 
Unikaalsed võtmed võivad koosneda mitmest veerust. Unikaalseid võtmeid nimetatakse ka alternatiivvõtmeteks. Unikaalsed võtmed on relatsiooni primaarvõtme alternatiiv. SQL-is on unikaalsetele võtmetele määratud UNIQUE piirang, et vältida duplikaate (duplikaatkirje ei ole unikaalses veerus kehtiv). 
Alternatiivseid võtmeid saab kasutada nagu primaarvõtit ühe tabeli valikul või WHERE-klausli filtreerimisel, kuid neid ei kasutata tavaliselt mitme tabeli ühendamiseks.

allikas:```https://en.wikipedia.org/wiki/Unique_key```

<img width="362" height="263" alt="{F01312B5-CF5B-4DE6-8500-3D466B6FC407}" src="https://github.com/user-attachments/assets/0614140d-8497-474d-800f-28049796ea10" />

## Simple Key
4.Lihtvõti (või aatomvõti) on primaarvõti, mis koosneb täpselt ühest veerust, et andmebaasi tabeli iga kirjet unikaalselt identifitseerida.

allikas:```https://annaabi.ee/andmebaasid-m47079.html?utm_source=```

<img width="316" height="239" alt="{A57A4E05-7D8B-4782-ABEA-1971122B1DFB}" src="https://github.com/user-attachments/assets/2da1f5ed-c679-473e-a926-a8dc565fa78e" />

## Composite Key
5.Andmebaasi kujundamisel on liitvõti kandidaatvõti, mis koosneb kahest või enamast atribuudist (tabeli veergudest), mis koos identifitseerivad unikaalselt üksuse esinemise (tabeli rea).

allikas:```https://en.wikipedia.org/wiki/Composite_key```

<img width="423" height="285" alt="{8045AB46-772A-4549-BEB7-F4D8808920B6}" src="https://github.com/user-attachments/assets/55a5cf2b-f989-4ff6-9923-263fdb85eb3b" />

## Compound Key
6.Seda aetakse sageli segi liitvõtmega, mille puhul kuigi tegemist on samuti võtmega, mis koosneb kahest või enamast atribuudist, mis identifitseerivad üksuse esinemise üheselt, ei ole vähemalt üks liitvõtme atribuut iseenesest lihtne võti.

allikas:```https://dba.stackexchange.com/questions/3134/in-sql-is-it-composite-or-compound-keys```

<img width="553" height="413" alt="{83A05DFF-A45F-49C6-A76D-46803BF1CE88}" src="https://github.com/user-attachments/assets/20bd615f-3f09-469e-8334-bfcdfea6b7f4" />

## Superkey
7.Relatsioonandmemudelis on supervõti mis tahes atribuutide kogum, mis identifitseerib unikaalselt iga relatsiooni tuupli. Kuna supervõtme väärtused on unikaalsed, peavad sama supervõtme väärtusega tuuplitel olema ka samad mitte-võtme atribuudi väärtused. 
See tähendab, et mitte-võtme atribuudid sõltuvad funktsionaalselt supervõtmest.

allikas:```https://en.wikipedia.org/wiki/Superkey```

<img width="444" height="234" alt="{612A8F45-5B11-47F2-B8B1-D7E58218FF4E}" src="https://github.com/user-attachments/assets/93d3264c-571b-4f62-ac7d-de098f67c906" />

## Candidate Key
8.Relatsioonandmebaasi kandidaatvõti ehk lihtsalt võti on mis tahes veergude kogum, millel on igas reas unikaalne väärtuste kombinatsioon, mille lisapiiranguks on see, et mis tahes veeru eemaldamine võib tekitada väärtuste duplikaate.

allikas:```https://en.wikipedia.org/wiki/Candidate_key```

<img width="375" height="256" alt="{96F21EC8-DC7B-4CAC-BE60-A41808B07B0A}" src="https://github.com/user-attachments/assets/a120ce7f-3fcb-4342-b6c6-62c08670e296" />

## Alternate Key
9.Alternatiivvõtmed on relatsioonandmebaasis olevad kandidaatvõtmed, mis identifitseerivad tabelis üheselt rea (tuple'i), kuid mida ei valita tabeli primaarvõtmeks. 
Need esindavad unikaalseid piiranguid, mis võiksid olla primaaridentifikaatoriks, kuid on määratud alternatiividena.

allikas:```https://www.quora.com/What-are-alternate-keys-in-a-database```

<img width="380" height="313" alt="{8A2CA277-361F-4BD8-907D-453DD86B2116}" src="https://github.com/user-attachments/assets/fd1afe89-447e-45c4-bdc5-cecdaee2d108" />


