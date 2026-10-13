# Slutprojekt - Kontaktbok

## Syfte och betygsmodell

Detta är ett av två alternativa slutprojekt. Projektet fördjupar standardcontainers, fil-I/O, robust inmatning, validering, sökning och testning. Projektets nivåer är **E -> C -> A**. Det finns ingen separat B-del i detta projekt.

## Uppgift

Det är mycket information som ska hållas ordning på för den moderna människan. Kontaktuppgifter för andra människor är en del av den. Som hjälpmedel har vi exempelvis Contacts i Googles GMail, Facebook
eller telefonböcker av alla de slag i mobiltelefonen. I detta projekt ska du få fördjupa dig i vad det krävs av ett program som ska hantera denna typ av information.

För betyget E krävs att du genomför grunduppgiften perfekt utan anmärkningar enligt angivna krav nedan. Vid tre eller fler anmärkningar ges betyget F.

For betygen C-A krävs de extrauppgifter som ges efter grunduppgiften. För ett betyg krävs att samtliga föregående (extra)uppgifter även är genomförda. (Även dessa ska vara utan anmärkningar, vid anmärkning sänks betyget fortfarande till F). Det går alltså inte uppfylla betyget A utan att uppfylla betyget C.

# E - Grunduppgift

- Skapa en grundläggande kontaktbok där man kan lagra och sedan ta fram information om kontakter.
  Den information som (minst) ska kunna lagras är
  • namn,
  • (post-) adress,
  • e-postadress,
  • telefonnummer,
  • födelsedag och
  • övrigt
  Gränssnittet ska fungera på följande sätt. Användaren ska kunna välja vad denne vill göra, exempelvis lägga till en kontakt eller hitta telefonnumret för en given kontakt. Det finns flera sätt att implementera detta, exempelvis:
  Att ha en meny där användaren får välja genom att mata in ett tal motsvarande ett av menyalternativen.
  Avsluta ska vara ett av alternativen.
  • Att ha ett kommandodrivet gränssnitt där användaren ger kommandon för vad som ska göras. Den funktionalitet och krav som ska finnas är:
- Lägga till kontakt.
- Ta bort kontakt.
- Söka efter kontakt och visa sökresultat tydligt.
- Spara kontaktboken i fil och återläs den vid nästa programstart.
- Minst en standardcontainer används meningsfullt.
- Samtliga obligatoriska fält bevaras vid spara/ladda.
- Container, kontaktidentitet och filformat dokumenteras.

Med **kontaktidentitet** menas:  **hur programmet entydigt avgör vilken kontakt användaren menar** , framför allt vid sökning och borttagning.

# C - Robusthet

Alla E-krav gäller dessutom.

- Felaktig meny-/kommandoindata hanteras kontrollerat.
- Sökning/borttagning av saknad kontakt hanteras tydligt.
- Saknad fil vid första körningen hanteras definierat.
- Korrupt/ofullständig kontaktfil upptäcks och rapporteras.
- En korrupt fil skrivs inte automatiskt över innan användaren informerats.
- Halvkonstruerade kontakter läggs inte in efter läsfel.

# A - Avancerad sökning och datavalidering

Alla E- och C-krav gäller dessutom.

## Sökning i alla fält

Söksträngen ska matchas mot namn, adress, e-post, telefon, födelsedag och övrigt. Textmatchning ska vara okänslig för versal/gemen, hitta delsträngar och kunna ge flera träffar.

## Validering

Tydliga, dokumenterade och testade regler ska finnas där det är rimligt. Minst:

- namn får inte vara tomt eller bara blanktecken,
- e-post ska följa en dokumenterad rimlig grundregel,
- födelsedag ska ha dokumenterat format och verkliga kalenderdatum ska valideras,
- andra rimliga begränsningar för projektets data ska definieras och motiveras.

## Filformat

Formatet ska entydigt kunna representera alla obligatoriska fält. Ta hänsyn till att adress och `övrigt` kan innehålla blanksteg och skiljetecken.

# Gemensamma krav som gäller hela projektet oavsett nivå

## Kod och struktur

- Inga globala variabler.
- Ingen `goto` för programflöde.
- Ingen `system("clear")`.
- Makefile är obligatorisk.
- För arbete över grunduppgiften ska koden vara lämpligt uppdelad i flera filer.
- Funktioner ska ha tydliga ansvar. Använd parametrar och returvärden där det är naturligt och undvik onödigt många parameterlösa `void`-funktioner.
- Temporära variabler ska vara så lokala som möjligt.
- Undvik kodupprepning och onödig hårdkodning.
- Programmet ska vara rimligt flexibelt och utbyggbart.

## Läsbarhet

- Använd beskrivande namn på variabler, funktioner och typer.
- Använd konsekvent språk och typografi.
- Egna funktioner ska kort kommenteras med syfte, parametrar och returvärde/relevant utdata.
- Kommentarer ska beskriva avsikt inte trivial C++-syntax.
- Extern hjälp som faktiskt används ska anges tydligt i källkoden vid den berörda lösningen.

## Användbarhet

Programmet ska vara självinstruerande. Användaren ska förstå vad programmet gör, vilken inmatning som förväntas och vad resultat eller felmeddelanden betyder. Inmatning ska inte göras onödigt komplicerad.

## C eller högre

Relevanta fel som användaren rimligen kan orsaka ska hanteras utan okontrollerad mjuk eller hård krasch. Felinmatningar och fellägen ska testas, inte bara normalfallet.

## A

Tydliga och rimliga begränsningar på indata ska finnas där validering är relevant. Reglerna ska vara dokumenterade, testade och möjliga att motivera.

## Nödvändigt för godkänt

1. Projektet uppfyller projektinstruktionen utan otillåten förenkling.
2. Studenten kan förklara alla detaljer i den kod som redovisas.

# Testning och redovisning

E ska testa tillägg, sökning, borttagning och full spara-starta om-ladda-kontroll. C ska dessutom testa felinmatning, saknad fil, korrupt/ofullständig fil och saknad kontakt. A ska testa delsträng i olika fält, versal/gemen samt giltiga och ogiltiga e-postadresser och kalenderdatum.

# Inlämning och redovisningsversion

Använd`kontakbok_inlamning_projektredovisning.pdf` för att lämna in följande information i Canvas senast dagen före redovisningen:

- valt projekt,
- önskad betygsnivå,
- GitHub-repository,
- taggen `presentation`,
- commit-ID.

Projektet och den version som studenten vill redovisa ska vara pushad till GitHub **senast dagen före den bokade redovisningen, vid deadline som anges i Canvas**. Deadline behövs för att läraren ska kunna planera redovisningen. Varje student disponerar **högst 10 minuter**.

Före deadline ska studenten committa och pusha redovisningsversionen samt skapa taggen `presentation`:

```bash
git status
git add .
git commit -m "Prepare project for presentation"
git push
git tag presentation
git push origin presentation
```

Kontrollera commit-ID:

```bash
git rev-parse presentation
```

Studenten får fortsätta arbeta efter deadline, men senare commits ingår inte automatiskt i redovisningsversionen. Flytta inte `presentation` efter deadline utan överenskommelse med läraren.

Projekt som inte registrerats i Canvas före deadline ingår normalt inte i planeringen för nästa dags redovisning och kan behöva redovisas vid ett senare tillfälle.
