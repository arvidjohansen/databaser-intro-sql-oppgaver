# Guide for oppsett av XAMP og basic bruk av SQL

For å kunne gjøre oppgavene som tar i bruk datasettet fått av lærer(Arvid), er det et par forutsetninger som må gjøres først.

Du må ha

- Code editor (feks vsCode)
- Relasjonsdatabase-server (MariaDB)
- Applikasjons-server (Apache)


Links til nedlastnings-sidene for Apache og MariaDB

- https://mariadb.com/downloads/
- https://www.apachelounge.com/download/

         Serverne ovenfor blir installert i en samlet pakke som heter XAMP, dette er programmet som vi skal bruke for å løse oppgavene, men å ha kjennskap til programmene som ligger bakom er smart for senere bruk.

 Her er link for hvor du kan nedlaste XAMP: https://www.apachefriends.org/download.html

---
# Guide for installasjon og oppsett
Etter du har installert XAMP med wizard får du opp et kontroll panel.

Her må du starte både Apache og MySQL, med START knappene. Deretter trykker du på ADMIN for å komme til phpMyAdmin siden.

På venstre side vil du se en liste med databaser, og på toppen er det et plus tegn hvor det står Ny, trykk på dette.

Så skriver du inn navnet på den nye databasen din og trykker opprett.

Nå vil du være inne i databasen din, deretter trykker du på en tab øverst på siden hvor det står, Importer.

Her legger du inn SQL filen du fikk av lærer(Arvid).

Nå vil du ha de nødvendige dataene for å kunne gjøre oppgavene.

---
# Guide for gjennomføring av oppgaver

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




