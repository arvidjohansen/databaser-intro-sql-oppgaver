# SQL-oppgaver

## Ressurser

1. [Forklaring av SQL-spørringer](https://docs.google.com/presentation/d/1QSET-BMSjlRSdELPgQuFouzDmxIH3SE9/edit?usp=sharing&ouid=104056741787912897114&rtpof=true&sd=true)
1. 

## Hvordan gå frem

Importer datasettet og finn SQL-koden som gir løsningen på følgende oppgaver:

``` 
1)	Hvor mange forskjellige skoler er det totalt?
2)	Hvor mange elever er det totalt?
3)	Hvor mange elever heter noe med «Hansen»?
4)	Hvilke elever har høyest karaktergjennomsnitt?
5)	Hva er gjennomsnittskarakteren for alle elevene?
6)	Hvilke elever har karaktergjennomsnitt mellom 3 og 4?
7)	Hvilke elever går på Valle Hovin VGS?	
8)	Hvor mange elever går på Oslo Katedralskole?
9)	Hvilken elev har høyest karaktergjennomsnitt på Etterstad?
10)	Hva er karaktergjennomsnittet på Nordre Aker Skole?
11)	Hvilken elev har lavest karaktergjennomsnitt på Hartvig Nissen?
12)	Hvilke skoler har ingen elever?
13)	Hvor mange elever går på skole utenfor Oslo?

Bonusoppgaver:
•	Hvilken skole har høyest karaktergjennomsnitt blant sine elever?
•	Hvilken skole har lavest karaktergjennomsnitt blant sine elever?
```

## Forklaring på SQL-koden som vi importerer

Fra /filer/utdanning.sql

Først lager vi databasen `utdanning` hvis den ikke allerede eksisterer:

```sql
CREATE DATABASE IF NOT EXISTS `utdanning` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
USE `utdanning`;
```

Lager elev-tabellen:
```sql
DROP TABLE IF EXISTS `elev`;
CREATE TABLE IF NOT EXISTS `elev` (
  `elevID` int(11) NOT NULL,
  `navn` varchar(255) DEFAULT NULL,
  `adresse` varchar(255) DEFAULT NULL,
  `gjennomsnitt` decimal(2,1) DEFAULT NULL,
  `skoleID` int(11) DEFAULT NULL,
  `postnr` varchar(4) DEFAULT NULL,
  PRIMARY KEY (`elevID`),
  KEY `skoleID` (`skoleID`),
  KEY `postnr` (`postnr`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

Setter inn data i elev-tabellen:
```sql
INSERT INTO `elev` (`elevID`, `navn`, `adresse`, `gjennomsnitt`, `skoleID`, `postnr`) VALUES
(1, 'Bror Hansen', 'Drammensveien 69', '5.0', 15, '1011'),
(2, 'Bouzian Ahmed', 'Lovisenberg DPS', '6.0', 6, '0045'),
(3, 'Bjarne Torsen', 'Skippergata 33', '5.0', 24, '1182'),
(4, 'Lisa Von Neuman', 'Drammensveien 39', '5.0', 7, '0364'),
(5, 'Magnus Carlsen', 'Drammensveien 126B', '3.0', 3, '0664'),
(6, 'Stig Roar Evjen', 'Frognerstranda 4', '4.0', 9, '1272'),
(7, 'Fredrik Staden', 'Postboks 4763', '2.0', 19, '1167'),
(8, 'Monica Dahl', 'Akersveien 24', '5.0', 2, '0791'),
(9, 'Jarand Severinsen', 'Postboks 1175', '5.0', 7, '0357'),
(10, 'Parsa Zadegan', 'Stortingsgata 30', '3.0', 3, '0686'),
(11, 'Lionel Messi', 'Møllerg. 16', '5.0', 4, '1152'),
(12, 'Mike Tyson', 'Drammensveien 74', '3.0', 1, '0139'),
(13, 'Joe Rogan', 'Drammensv. 82', '5.0', 20, '0594'),
(14, 'Khabib Nurmagomedov', 'Wergelandsveien 7', '4.0', 14, '0457'),
(15, 'Eric Clapton', 'Meltzersgate 5', '4.0', 7, '0682'),
(16, 'Hans Safari', 'Wergelandsveien 15', '4.0', 20, '0250'),
... (flere rader)
``` 

Lager postnummer-tabellen:
```sql
DROP TABLE IF EXISTS `postnummer`;
CREATE TABLE IF NOT EXISTS `postnummer` (
  `Pnr` varchar(4) NOT NULL,
  `sted` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`Pnr`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```


Setter inn data i postnummer-tabellen:
```sql
INSERT INTO `postnummer` (`Pnr`, `sted`) VALUES
('0001', 'OSLO'),
('0010', 'OSLO'),
('0015', 'OSLO'),
('0018', 'OSLO'),
('0021', 'OSLO'),
('0024', 'OSLO'),
('0026', 'OSLO'),
('0028', 'OSLO'),
('0030', 'OSLO'),
('0031', 'OSLO'),
('0032', 'OSLO'),
('0033', 'OSLO'),
('0034', 'OSLO'),
('1890', 'RAKKESTAD'),
('1891', 'RAKKESTAD'),
('1892', 'DEGERNES'),
('1893', 'DEGERNES'),
('1894', 'RAKKESTAD'),
('1900', 'FETSUND'),
('1901', 'FETSUND'),
('1903', 'GAN'),
... (over 5000 rader)
```


Lager skole-tabellen:
```sql
DROP TABLE IF EXISTS `skole`;
CREATE TABLE IF NOT EXISTS `skole` (
  `skoleID` int(11) NOT NULL,
  `navn` varchar(255) DEFAULT NULL,
  `adresse` varchar(255) DEFAULT NULL,
  `postnr` varchar(4) DEFAULT NULL,
  PRIMARY KEY (`skoleID`),
  KEY `postnr` (`postnr`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

```


Setter inn data i skole-tabellen:
```sql
INSERT INTO `skole` (`skoleID`, `navn`, `adresse`, `postnr`) VALUES
(1, 'Bjerke videregående skole ', 'Statsråd Mathisens vei 25', '0594'),
(2, 'Bjørnholt videregående skole ', 'Slimeveien 15 - 17', '1275'),
(3, 'Blindern videregående skole ', 'Sognsveien 80', '0855'),
(4, 'Edvard Munch videregående skole ', 'Ullevålsveien 5', '0165'),
(5, 'Eikelund videregående skole ', 'Nydalsveien 30b', '0484'),
(6, 'Elvebakken videregående skole ', 'Vestre Elvebakke 3', '0182'),
(7, 'Etterstad videregående skole ', 'Etterstadsletta 5', '0660'),
(8, 'Foss videregående skole ', 'Steenstrups gate 20', '0554'),
(9, 'Fyrstikkalleen skole ', 'Fyrstikkalleen 21', '0661'),
(10, 'Hartvig Nissens skole ', 'Niels Juels gate 56', '0259'),
(11, 'Hellerud videregående skole ', 'Wilhelm Stenersens vei 6', '0671'),
(12, 'Hersleb videregående skole ', 'Herslebs gate 20 B', '0561'),
(13, 'Holtet videregående skole ', 'Ekebergveien 124', '1178'),
(14, 'Kirkeveien videregående skole ', 'Lille Ullevål Ullevål sykehus', '0450'),
(15, 'Kongshavn videregående skole ', 'Kongsveien 30', '0193'),
(16, 'Kongsskogen videregående skole ', 'Gladengveien 3B', '0661'),
... (flere rader)
```

Legger på Foreign key (fremmednøkkel-kobling) på elev, og skole-tabellen:
```sql
ALTER TABLE `elev`
  ADD CONSTRAINT `elev_ibfk_1` FOREIGN KEY (`skoleID`) REFERENCES `skole` (`skoleID`),
  ADD CONSTRAINT `elev_ibfk_2` FOREIGN KEY (`postnr`) REFERENCES `postnummer` (`Pnr`);
```


## For å kunne gjøre oppgavene må du

1. Installere XAMPP
1. Åpne PHPMyAdmin
1. Importere datasettet fra `utdanning.sql`
1. Bekreft at dataimporten har gått bra (du skal se en ny database som heter `utdanning` på venstre side)
1. Trykk på SQL-fanen og skriv SQL-koden som må til for å løse oppgavene


 Link til nedlasting av XAMPP: https://www.apachefriends.org/download.html

---
# Guide for installasjon og oppsett (laget av Vilmer)
Etter du har installert XAMP med wizard får du opp et kontroll panel.

Her må du starte både Apache og MySQL, med START knappene. Deretter trykker du på ADMIN for å komme til phpMyAdmin siden.

På venstre side vil du se en liste med databaser, og på toppen er det et plus tegn hvor det står Ny, trykk på dette.

Så skriver du inn navnet på den nye databasen din og trykker opprett.

Nå vil du være inne i databasen din, deretter trykker du på en tab øverst på siden hvor det står, Importer.

Her legger du inn SQL filen du fikk av lærer(Arvid).

Nå vil du ha de nødvendige dataene for å kunne gjøre oppgavene.

---
# Guide for gjennomføring av oppgaver (laget av Vilmer)

Når du er inne i databasen din trykker du på SQL tabben for å kunne skrive spørringer mot databasen.

La oss gjennomgå første oppgave.

Hvor mange forskjellige skoler er det totalt?

Her er en liste over kommandoer du trenger for å løse oppgaven.

---
SELECT: Henter data fra en spesifisert gruppe, enten kan man hente all data eller noe spesifikt (WHERE).

*(stjernetegn): Alle rader i en tabell. 

FROM: Beskriver hvilken tabell man skal hente data fra.

COUNT: Returnerer hvor mange rader som matcher et satt kriterie.

---
## LØSNING

>! SELECT COUNT(*) FROM skole;

---

# Guide for å kjøre og vise SQL i VScode

- Gå til extensions, søk MySQL (Wejian Chen), installer den.
- Trykk på Database tabben i VScode på venstre siden.
- Trykk på new connection.
- Hent port nummer fra MySQL config filen i XAMP.
- Opprett connection
- Opprett nytt SQL dokument
- GO WILD




