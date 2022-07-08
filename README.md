--I4
--1
SELECT * FROM Stavka
WHERE PopustUPostocima > 0.04
ORDER BY RacunID DESC

--2
UPDATE Proizvod
SET 
	CijenaBezPDV = CijenaBezPDV * 0.10,
	BrojProizvoda = BrojProizvoda + '-B'
WHERE Boja LIKE '%Plava'

--3
-- ID 1
-- ID RACUN 75124
-- ID PROIZVOD 856

INSERT INTO Racun (DatumIzdavanja, BrojRacuna, KupacID)
VALUES('2022-07-06', 'SO42069', 1)

INSERT INTO Stavka (RacunID, Kolicina, ProizvodID, CijenaPoKomadu, PopustUPostocima, UkupnaCijena)
VALUES (75124, 2, 856, 50, 0.25, 75)

--4
DELETE FROM Proizvod
WHERE Boja LIKE '%Crna' AND PotkategorijaID IS NULL

--5
-- GRADID 1
Select * From Grad
Select * FROM Kupac

DELETE Telefon FROM Kupac
WHERE GradID = 1

-- 6
--IDKUPAC 156
DELETE FROM Stavka
WHERE RacunID = 69461

DELETE  FROM Racun
WHERE KupacID = 156

DELETE FROM Kupac
WHERE Ime LIKE '%Gustavo'

--7
SELECT k.Naziv AS Kategorija, p.Naziv as Proizvod from Proizvod as p
INNER JOIN Potkategorija as pk ON pk.IDPotkategorija = p.PotkategorijaID
INNER JOIN Kategorija as k ON k.IDKategorija = pk.KategorijaID
WHERE k.Naziv IN ('Tights', 'Dijelovi')

--8
SELECT r.BrojRacuna, r.KreditnaKarticaID, kr.Broj as BrojKreditneKartice FROM Racun as r
FULL OUTER JOIN KreditnaKartica as kr ON r.KreditnaKarticaID = kr.IDKreditnaKartica
WHERE KreditnaKarticaID  IS NULL

--9
SELECT r.BrojRacuna, k.Tip FROM KreditnaKartica as k
RIGHT OUTER JOIN Racun as r on k.IDKreditnaKartica = r.KreditnaKarticaID
ORDER BY k.Tip ASC

--10
SELECT kom.Ime, kom.Prezime, r.KomercijalistID, r.DatumIzdavanja FROM Komercijalist as kom
FULL OUTER JOIN Racun as r ON r.KomercijalistID = kom.IDKomercijalist
WHERE r.KomercijalistID IS NULL	

--11

SELECT r.BrojRacuna, p.Naziv, s.Kolicina, kk.Broj FROM Racun as r
LEFT JOIN Stavka as s on s.RacunID =r.IDRacun
LEFT JOIN Proizvod as p on p.IDProizvod = s.ProizvodID
LEFT JOIN KreditnaKartica as kk on kk.IDKreditnaKartica = r.KreditnaKarticaID
WHERE r.KreditnaKarticaID IS NULL OR r.KreditnaKarticaID IS NOT NULL

--ISHOD 5

--1
SELECT k.Ime, k.Prezime + '...' as Prezime
FROM Kupac as k
WHERE LEN(k.Prezime) > 5

--2
SELECT max(DATEDIFF(year, r.DatumIzdavanja, GETDATE())) AS Razlika, min(DATEDIFF(year, r.DatumIzdavanja, GETDATE())) AS Razlika
FROM Racun AS r

--3
SELECT COUNT(*) as IzdaniRacuni, SUM(s.UkupnaCijena) as UkupnaCijena FROM Racun as r
INNER JOIN Stavka AS s ON s.RacunID = r.IDRacun
WHERE DATEPART(month, r.DatumIzdavanja) > 9

--4
SELECT DISTINCT kom.Ime, kom.Prezime AS ImePrezime, SUM(s.UkupnaCijena) as UkupnaCijena
FROM Komercijalist as kom
INNER JOIN Racun as r ON r.KomercijalistID = kom.IDKomercijalist
INNER JOIN Stavka as s ON s.RacunID = r.IDRacun
WHERE DATEPART(WEEKDAY, r.DatumIzdavanja) = 7
GROUP BY kom.Ime, kom.Prezime
HAVING SUM(s.UkupnaCijena) > 2000


-- ISHOD 6
--1
SELECT r.IDRacun,(
	SELECT AVG(s.UkupnaCijena)
	FROM Stavka as s
	WHERE s.RacunID IN (
		SELECT r1.IDracun
		FROM Racun as r1
		WHERE r1.IDRacun = r.IDRacun)) as Prosjek
		FROM Racun as r

--2
SELECT DISTINCT kk.Tip
FROM KreditnaKartica as kk
WHERE kk.IDKreditnaKartica IN (
	SELECT r.KreditnaKarticaID
	FROM Racun as r
	WHERE r.IDRacun IN (
		SELECT s.RacunID
		FROM Stavka as s
		WHERE s.ProizvodID IN (
		SELECT p.IDProizvod
		FROM Proizvod AS p
		WHERE p.Boja='crna'
		)
	)
)

--3
SELECT DISTINCT p.Naziv,
(
	SELECT SUM(st.Kolicina)
	FROM Stavka as st
	WHERE st.ProizvodID = p.IDProizvod
) AS BrojProizvoda
FROM Proizvod as p
WHERE
(
	SELECT sum(st.Kolicina)
	FROM Stavka as st
	WHERE st.ProizvodID = p.IDProizvod
) is not null

ORDER BY 2 DESC 



--4
SELECT kom.Ime, kom.Prezime, COUNT(r.IDRacun) 'Broj računa'
FROM Komercijalist AS kom
INNER JOIN Racun AS r ON kom.IDKomercijalist = r.KomercijalistID
GROUP BY kom.Ime, kom.Prezime HAVING COUNT(*) >
(
	SELECT AVG(temp.broj_racuna_po_komercijalistu) FROM
	(
		SELECT COUNT(r.IDRacun) AS broj_racuna_po_komercijalistu
		FROM Komercijalist as kom INNER JOIN Racun AS r ON kom.IDKomercijalist = r.KomercijalistID
		GROUP BY kom.Ime, kom.Prezime
	) AS temp
)
