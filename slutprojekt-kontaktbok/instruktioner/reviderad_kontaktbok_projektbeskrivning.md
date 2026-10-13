# Projekt: Kontaktbok

## Kursprojekt i C++

---

# 1. Syfte

Projektet syftar till att ge praktisk erfarenhet av programmering genom att sammanföra flera av kursens centrala moment i ett större sammanhängande program.

Genom projektet ska studenten:

- tillämpa datastrukturer för lagring av information,
- arbeta med filhantering,
- hantera användarinmatning och validering,
- implementera felhantering,
- strukturera kod i funktioner och moduler,
- utveckla och testa ett komplett program.

Projektet ska ge erfarenhet av att utveckla ett program som kan användas över tid där data sparas mellan körningar.

---

# 2. Projektbeskrivning

Du ska utveckla en kontaktbok för lagring och hantering av personkontakter.

Programmet ska kunna lagra information om personer, spara informationen till fil och läsa tillbaka informationen vid senare programkörningar.

När programmet avslutas ska alla ändringar bevaras.

---

# 3. Obligatoriska funktioner

Minimikrav för godkänt projekt.

Programmet ska kunna:

1. Lägga till ny kontakt.
2. Ta bort kontakt.
3. Söka efter kontakt.
4. Visa alla kontakter.
5. Spara kontaktboken till fil.
6. Läsa in kontaktboken från fil.
7. Avsluta programmet på ett kontrollerat sätt.

---

# 4. Information som ska lagras

Varje kontakt ska innehålla minst:

- Förnamn
- Efternamn
- Telefonnummer
- E-postadress
- Födelsedatum

Ytterligare fält får läggas till.

---

# 5. Kontaktidentitet

Projektet ska dokumentera hur en kontakt identifieras.

Om flera kontakter kan ha samma namn måste programmet kunna hantera detta på ett entydigt sätt.

Vald lösning ska beskrivas i README.md.

---

# 6. Datastrukturer

Minst en lämplig standardcontainer från STL ska användas.

Exempel:

- `std::vector`
- `std::map`
- `std::multimap`

Studenten ska kunna motivera sitt val av datastruktur.

---

# 7. Filhantering

Programmet ska kunna:

- spara kontaktboken till fil,
- läsa kontaktboken från fil,
- återställa tidigare sparad information.

CSV, TXT, JSON eller eget format är tillåtet om formatet dokumenteras.

---

# 8. Validering

Programmet ska validera användarens inmatning.

## E-postadress

Ska innehålla lokal del, @-tecken och domändel.

## Födelsedatum

Ska följa dokumenterat format och representera ett giltigt kalenderdatum.

## Telefonnummer

Valideringsregler ska dokumenteras.

---

# 9. Felhantering

Programmet ska hantera fel på ett kontrollerat sätt och ge begripliga felmeddelanden.

---

# 10. Korrupt eller ofullständig fil

Programmet ska upptäcka korrupta eller ofullständiga filer.

Vid upptäckt ska programmet:

1. Informera användaren.
2. Undvika okontrollerad krasch.
3. Inte skriva över befintlig data utan användarens vetskap.

---

# 11. Stabilitet

Programmet ska vara robust.

## Hård krasch

Programmet avslutas oväntat.

## Mjuk krasch

Programmet fortsätter köra men hamnar i ett felaktigt tillstånd.

---

# 12. Menysystem

Programmet ska ha ett användarvänligt menysystem som fortsätter visas tills användaren väljer att avsluta programmet.

---

# 13. Kodkvalitet

Koden ska vara läsbar, konsekvent strukturerad och rimligt kommenterad.

---

# 14. Dokumentation

Projektet ska innehålla en README.md med:

- projektbeskrivning
- bygginstruktion
- körinstruktion
- datastruktur
- kontaktidentitet
- filformat
- valideringsregler
- kända begränsningar

---

# 15. Versionshantering

Projektet ska lagras i ett Git-repository med rimlig commit-historik.

---

# 16. Testning

Minst följande scenarier ska testas:

- lägga till kontakt
- ta bort kontakt
- söka kontakt
- spara data
- läsa tillbaka data
- felaktig e-postadress
- felaktigt datum
- korrupt datafil

---

# 17. Redovisning

Studenten ska kunna:

- demonstrera programmets funktioner
- beskriva vald datastruktur
- förklara filhanteringen
- beskriva valideringsreglerna
- visa hur fel hanteras
- motivera designval

---

# 18. Betygskriterier

## Betyg E

- uppfyller samtliga obligatoriska krav
- kan spara och läsa data
- har grundläggande validering

## Betyg C

- välstrukturerad kod
- god felhantering
- tydlig dokumentation
- väl genomförd testning

## Betyg A

- mycket robust lösning
- hög kodkvalitet
- omfattande testning
- användarvänligt gränssnitt

---

# Rekommenderade teorimoment från kursen

- funktioner
- struct
- STL-containrar
- fstream
- sökning och sortering
- felhantering
- modulär programdesign
- Git
