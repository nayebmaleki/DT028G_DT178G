# Projekt: En kontaktbok

## Introduktion till programmering i C++

## 1. Introduktion

Det är mycket information som den moderna människan behöver hålla ordning på. Kontaktuppgifter till andra människor är en del av denna information. Som hjälpmedel finns exempelvis Google Contacts, Facebook och olika typer av telefonböcker i mobiltelefoner.

I detta projekt ska du fördjupa dig i vad som krävs av ett program som hanterar kontaktinformation.

## 2. Syfte

Syftet med projektet är att fördjupa dina kunskaper i programmering och utveckla din programmeringsvana. Du ska också få fördjupade kunskaper om hur datastrukturer som behandlats under kursen kan användas i ett sammanhängande program.

## 3. Teori

Datastrukturer och delar av C++-standardbiblioteket som kan vara användbara i projektet är bland annat:

- `std::map` eller `std::multimap`
- `std::vector`
- `std::fstream`
- `struct`

Du behöver inte använda samtliga alternativ i listan. Du ska däremot använda minst en container i grunduppgiften.

## 4. Uppgift och betygssteg

Projektet är uppdelat i olika betygssteg.

- För betyget **E** ska grunduppgiften genomföras enligt kraven i avsnitt 4.1.
- För betyget **C** ska både grunduppgiften och extrauppgift C vara genomförda.
- För betyget **A** ska grunduppgiften, extrauppgift C och extrauppgift A vara genomförda.

Ett högre betyg förutsätter alltså att samtliga krav för de lägre betygsstegen också är uppfyllda. Projektet granskas med hjälp av det granskningsprotokoll som finns på lärplattformen. Anmärkningar som framkommer vid granskningen ska åtgärdas före inlämning och redovisning.

## 4.1 Grunduppgift, betyg E

Skapa en grundläggande kontaktbok där användaren kan lagra och senare ta fram information om kontakter.

### Kontaktinformation

För varje kontakt ska minst följande information kunna lagras:

- namn
- postadress
- e-postadress
- telefonnummer
- födelsedag
- övrig information

Med **övrig information** menas ett fält där användaren kan lagra annan valfri information om kontakten.

### Gränssnitt

Användaren ska kunna välja vilken åtgärd som ska utföras. Gränssnittet kan exempelvis utformas på något av följande sätt:

- En meny där användaren matar in ett tal som motsvarar ett menyalternativ.
- Ett kommandodrivet gränssnitt där användaren skriver kommandon för de åtgärder som ska utföras.

Programmet ska ha ett tydligt alternativ eller kommando för att avsluta.

### Obligatorisk funktionalitet

Programmet ska kunna:

- lägga till en kontakt
- ta bort en kontakt
- söka efter en kontakt

När en sökning ger en eller flera träffar ska den lagrade informationen om de matchande kontakterna visas tydligt.

### Lagring i fil

Kontaktboken ska sparas i en fil så att kontakterna finns kvar mellan programkörningarna. Det innebär att programmet ska kunna:

- skriva kontaktinformationen till en fil
- läsa tillbaka den sparade kontaktinformationen vid en senare körning

Samtliga obligatoriska kontaktfält ska finnas kvar efter att kontaktboken har sparats, programmet har avslutats och filen har lästs in igen.

### Container

För grunduppgiften ska minst en container användas för att lagra kontakterna under programmets körning, exempelvis `std::vector`, `std::map` eller `std::multimap`.

## 4.2 Extrauppgift C, robusthet

Utöver samtliga krav för grunduppgiften ska programmet vara robust mot fel som användaren rimligen kan orsaka.

Programmet ska inte kunna försättas i en mjuk eller hård krasch genom felaktig inmatning.

### Hård krasch

En hård krasch innebär att programmet avslutas oväntat på grund av ett fel. Om användaren exempelvis matar in fel typ av data ska programmet inte avslutas, utan informera användaren om felet och ge möjlighet att göra ett nytt försök.

### Mjuk krasch

En mjuk krasch innebär att programmet fortsätter att köra men hamnar i ett felaktigt eller obrukbart tillstånd. Ett exempel är att samma felmeddelande skrivs ut om och om igen i en loop utan att användaren kan komma vidare.

### Fel i kontaktbokens fil

Om filen med kontaktinformation är korrupt eller har ett format som programmet inte kan läsa ska programmet:

- informera användaren om att något är fel
- tydligt ange att kontaktboken inte kunde laddas
- fortsätta eller avsluta på ett kontrollerat sätt utan att krascha

Med en **korrupt fil** menas här en fil vars innehåll inte följer det format som programmet förväntar sig, exempelvis därför att information saknas eller är felaktigt strukturerad.

## 4.3 Extrauppgift A, avancerad sökning och validering

Utöver samtliga krav för grunduppgiften och extrauppgift C ska programmet uppfylla följande krav.

### Sökning i alla fält

Programmet ska söka efter söksträngen i samtliga kontaktfält:

- namn
- postadress
- e-postadress
- telefonnummer
- födelsedag
- övrig information

Sökningen ska:

- vara okänslig för skillnaden mellan versaler och gemener
- hitta söksträngen som en del av ett längre fältvärde
- kunna visa flera matchande kontakter

Om användaren exempelvis söker efter `ada` ska programmet kunna hitta namn som `Ada Arvidsson`, `Adam Allsing` och `Cecilia Adamsdotter`. Eftersom sökningen ska göras i alla fält ska även kontakter vars adress innehåller exempelvis `Ada Lovelaces väg` eller vars postort är `Adamstorp` kunna visas.

### Validering av kontaktinformation

Programmet ska ha tydliga och rimliga begränsningar för den kontaktinformation som användaren kan mata in.

Exempel på sådan validering är:

- En e-postadress ska innehålla tecknet `@`.
- En födelsedag ska följa ett bestämt och giltigt format.

Programmet ska informera användaren när inmatningen inte följer reglerna och ge möjlighet att mata in informationen på nytt.

## 5. Examination

Det färdiga projektet ska först granskas, helst av en annan student på kursen, med hjälp av granskningsprotokollet på lärplattformen.

Om kamratgranskning inte är möjlig kan du själv gå igenom granskningsprotokollet och kontrollera samtliga punkter som projektet ska uppfylla.

Efter granskningen ska du åtgärda de påpekanden som har framkommit.

Projektet ska därefter lämnas in senast dagen före angiven deadline för att det ska finnas tid att planera redovisningen enligt det schema och den grupp du tillhör.

Inlämningen ska endast innehålla:

- källkod
- byggskript

Följ alltid de aktuella inlämningsanvisningarna på lärplattformen.

## 6. Ursprung och licens

Uppgiften i sin originalform skapades av Daniel Bosk.

Verket är tillgängliggjort under licensen Creative Commons Erkännande-DelaLika 2.5 Sverige, CC BY-SA 2.5 SE.
