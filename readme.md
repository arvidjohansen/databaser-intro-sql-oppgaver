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

For å kunne gjøre oppgavene må du

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




