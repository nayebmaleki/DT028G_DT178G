# Slutprojekt - Bulls and Cows

## Syfte och betygsmodell

Detta är ett av två alternativa slutprojekt. Projektet fördjupar algoritmer, datastrukturer, funktionsuppdelning, robust inmatning, filhantering och testning. Betygsnivåerna är kumulativa: **E -> C -> B -> A**.

## Introduktion och spelregler

Bulls and Cows, av vilket Mastermind är en känd variant, är ett klassiskt kodknäckningsspel för två spelare där det går ut på att gissa sig vilket tal som motståndaren tänker på. De två rollerna i spelet är alltså en kodmakare, som hittar på talet, och en kodknäckare, som ska lista ut talet.
Spelet fungerar enligt följande. Jag tänker på ett fyrsiffrigt tal där varje siffra endast får förekomma en gång, upprepningar är alltså inte tillåtna, och du ska gissa på vilket tal det är. Utifrån din gissning svarar jag med ett antal bulls eller cows. Du får en bull för varje siffra i talet som är på rätt plats och en cow för varje siffra som är rätt men på fel plats.

 (Notera att du inte får veta vilka tal som gav dig bull eller cow.) För siffror som inte är med i talet får du ingenting. Därefter får du gissa igen utifrån den information du har fått. Detta illustreras enklast
med ett exempel.
Exempel 1. Jag tänker på talet 1234. Din första gissning är 1437. Du får då som svar **two bulls** för ettan och trean,
och du får **one cow** för fyran. Du gissar härnäst på 2437 och får då svaret **one bull** för trean och **two cows** för tvåan och fyran. Sedan fortsätter spelet tills du fått **four bulls** som svar.
Notera återigen att du inte får veta för vilka siffror du får bulls respektive cows, detta får du veta här enbart för att exemplet ska vara tydligt.
Det finns lite olika angripssätt för att lista ut talet, se avsnitt 3, och i detta projekt kommer du att titta på ett av dem, men fokus kommer att ligga på att implementera spelet.

Notera att Mastermind och Bulls and Cows skiljer sig något. I Bulls and Cows får siffrorna inte upprepas,
vilket de får göra i Mastermind. I Mastermind används också (oftast) bara talen 1-6 medan talen 0-9 används i Bulls and Cows.

I detta projekt ska du till en början titta på en enkel algoritm för att lösa problemet, den algoritm du ska använda dig av ges nedan.
Algoritmen har funktionen GenereraGissning för att generera en gissning utifrån tidigare gissningar, eller en
initial gissning om inga tidigare gissningar finns. Algoritmen garanteras avslut om gissningarna och svaren i mängden G stämmer överens. Exempelvis om kodmakaren fuskar genom att under spelets gång byta sitt hemliga tal är resultatet av algoritmen odefinierat.

Följa algoritmen steg för steg och koppla pseudokoden till motsvarande C++-kod.

## Given algoritm

```text
FUNCTION BullsCows(x, y)
    RETURN antalet bulls och cows när x jämförs med y
END FUNCTION

FUNCTION GiltigGissning(g, G)
    FOR varje (gi, ai) i G
        IF BullsCows(g, gi) != ai
            RETURN false
        END IF
    END FOR
    RETURN true
END FUNCTION

FUNCTION GenereraGissning(G)
    IF G är tom
        g = 1023
    ELSE
        g = nästa kandidat efter den största tidigare gissningen
    END IF

    flytta g till en kod med fyra distinkta siffror om det behövs

    WHILE GiltigGissning(g, G) == false
        flytta g till nästa kod med fyra distinkta siffror
    END WHILE

    RETURN g
END FUNCTION
```

# E - Grunduppgift

- I grundutförandet ska du implementera en version av spelet där programmet gissar på talet som användaren tänker på. Det vill säga programmet agerar kodknäckare och användaren kodmakare. Detta kan du göra genom att implementera algoritmen ovan. Användaren tänker alltså på ett tal, programmet skriver ut gissningarna på skärmen och användaren matar in antalet bulls och cows.

# C - Robusthet och motsägelsekontroll

Alla E-krav gäller dessutom,

Ditt program ska ha felhantering. Det ska kunna detektera när användaren har fuskat (eller bara tänkt fel) för att programmet inte ska fortsätta i all evighet. En lösning i likhet med att införa en maxgräns på 1000 gissningar är dock inte giltig, programmet ska säga till precis när det går att avgöra att användaren gjort fel – helst med en kommentar i stil med Ye cheatin’ scum!.
Med felhantering menas även att programmet ska hantera om en användare matar in fel, exempelvis om denne matar in bokstäver där det förväntas heltal. Detta betyder att varken mjuk eller hård krash uppstå. Mjuk krash betyder att programmet ger varningar eller felmeddelanden men fortsätter att exekvera (felhantering inte gjorts på rätt sätt). Hård krash betyder att programmet avslutas helt pga. fel. Därför skall du testa ditt prgram för alla typer av inmatningar.

# B - Ombytta roller och highscore

Alla E- och C-krav gäller dessutom,

- Utöka ditt program så att användaren kan agera kodknäckare och programmet är kodmakare, det vill säga ombytta roller jämfört med grunduppgiften. Du ska även skapa en highscorelista.
- Highscorelista dokumenteras i `student_arbete/README.md`.

# A - Fördjupning

Alla E-, C- och B-krav gäller dessutom. Genomför minst ett alternativ fullständigt:

1. **Självspel och statistik:** låt programmet spela mot sig självt och redovisa vilka koder som är svårast enligt tydligt definierade mått.
2. **Förbättrad algoritm/strategi:** implementera och jämför en bättre strategi empiriskt med grundalgoritmen på samma testmängd.
3. **Kommandoradsgränssnitt:** relevanta val kan anges via argument, `--help` finns och felaktiga argument hanteras kontrollerat. Du kan använda biblioteket getopt(3). Exempelvis om den exekverbara filen heter bullcow och vi vill specificera att highscorelistan ska
   lagras i filen highscore.txt: `$ ./bullcow -f highscore.txt`

Vald A-fördjupning ska verifieras med test eller mätning.

# Gemensamma krav som gäller hela projektet

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
- Kommentarer ska förklara **varför** koden finns och  **hur den ska användas** , inte beskriva sådant som redan är uppenbart från själva koden (dvs. inte trivial C++-syntax).
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

# Inlämning och redovisningsversion

Använd`Bullcow_inlamning_projektredovisning.pdf` för att lämna in följande information i Canvas inför redovisningen:

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
