# Labb 1

# MySQL

Skärmdump som visar database explorer i IntelliJ med skapad person-tabell med data:

![MySQL i database explorer](bilder/bild2.png)

NOT: Ni ska även ha skapat en user som bara har access till databasen my_database, ingen bild krävs

# MongoDB

Skärmdump av databas på MongoDB Atlas med skapad movie-collection med data:

![MongoDBAtlas](bilder/bild3.png)

# SQL

Skärmdump som visar att ni klarat av första två sidorna på sqlbolt.com:s interaktiva tutorial

![SQL-bolt](bilder/bild4.png)
![SQL-bolt](bilder/bild5.png)

# Frågor som ni ska svara på (G-nivå)

Besvara frågorna med egna ord. Ge gärna exempel.

## Databaser och verktyg

1. Vad är en databas, och vad kan den användas till? En databas är ett organiserat sätt att lagra data så att den kan
   sparas permanent, sökas, ändras och delas
2. Vad används språket SQL till?

## Tabeller och relationer

3. Vad är en tabell, en rad och en kolumn? En tabell samlar information om en sak (t.ex. person), en rad är en specifika
   instans av en person och en kolumn är en egenskap (t.ex. förnamn).
4. Vad är en primärnyckel, och varför behövs den? En primärnyckel är en kolumn som unikt identifierar varje rad
5. Vad är en främmande nyckel? En främmande nyckel är en kolumn som refererar till en primärnyckel i en annan tabell,
   vilket skapar en relation mellan tabellerna.
6. Varför är det bra att lagra kunduppgifter och köp i olika tabeller? Då slipper man upprepa kunduppgifter på varje
   köp. Det sparar plats, minskar risken för fel och gör att en ändring bara behöver göras på ett ställe.

## NoSQL

7. Vad menas med NoSQL, och hur kan information organiseras i en sådan databas? NoSQL är databaser som inte använder
   tabeller med fasta kolumner. Data organiserar på andra sätt såsom redis använder en nyckel-värde struktur
8. Ge ett exempel på när en NoSQL-databas kan vara lämplig och förklara varför. Ett exempel när man använder en NoSQL
   databas kan vara när man använder t.ex. cassandraDb som är en kolumnbaserad databas. Den är bra när man har mycket
   data som inte behöver vara strikt strukturerad och där man vill kunna skala ut horisontellt. Exempelvis kan det vara
   användbart för loggdata eller realtidsanalyser där man snabbt behöver skriva och läsa stora mängder data utan att
   behöva definiera ett fast schema.

## SQL – hämta data från tabellen person

Skriv en SQL-fråga som svar på varje uppgift.

9. Hämta alla kolumner för alla personer i tabellen.
   ```SQL
   SELECT * FROM person;
   ```

10. Hämta endast förnamn och efternamn för alla personer.
   ```SQL
   SELECT firstName, lastName FROM person;
   ```

11. Hämta förnamn, efternamn och inkomst för personer med en inkomst över 30 000.
   ```SQL
   SELECT firstName, lastName, income FROM person WHERE income > 30000;
   ```

12. Hämta alla personer födda före den 1 januari 1990.
   ```SQL
   SELECT * FROM person WHERE birthDate < '1990-01-01';
   ```

13. Hämta förnamn, efternamn och inkomst, sorterat efter inkomst från högst till lägst.
   ```SQL
   SELECT firstName, lastName, income FROM person ORDER BY income DESC;
   ```

14. Räkna hur många personer som finns i tabellen.
   ```SQL
   SELECT COUNT(*) FROM person;
   ```

# VG-nivå

Dessa frågor ska besvaras med ett längre svar, minst en halv A4-sida:

1. En banköverföring avbryts efter att pengarna dragits från det första kontot. Vad kan konsekvensen bli, och hur kan en
   transaktion hjälpa? En transaktion i en databas är användbar när det krävs att massor av instruktioner ska utföras
   som en enstaka operation. Om en banköverföring avbryts efter att pengarna dragits från det första kontot, men innan
   de har lagts till på det andra kontot, kan det leda till att pengarna försvinner från det första kontot utan att
   någonsin nå det andra kontot. Detta kan skapa problem för både banken och kunden. Genom att använda en transaktion
   kan man säkerställa att antingen alla steg i överföringen lyckas eller att ingen av dem gör det. Om något går fel
   under processen, kan transaktionen rullas tillbaka, vilket innebär att pengarna återförs till det första kontot och
   inga pengar förloras.

2. Välj ett enkelt system, antingen en webbutik eller en chatt. Resonera om när en relationsdatabas respektive en
   NoSQL-databas kan vara lämplig. Motivera med hur informationen ska lagras och användas. Jag skulle aldrig använda en
   relationsdatabas för t.ex. rate-limiting i en chattapplikation. Det är bättre att använda en NoSQL-databas som t.ex.
   Redis för att lagra information om användares aktivitet och begränsa antalet meddelanden de kan skicka under en viss
   tidsperiod. Detta beror på att rate-limiting kräver snabb åtkomst och uppdatering av data, vilket NoSQL-databaser är
   optimerade för.


