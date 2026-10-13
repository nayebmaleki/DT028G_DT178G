# Laboration 1 - Min, max och medelvärde

## Tema
Iteration, selektion, aritmetik, standard input, omdirigering, systematisk testning och Git.

## Bakgrund
En stor mängd data behöver inte alltid lagras i minnet för att kunna bearbetas. I denna laboration ska du läsa en följd av heltal ett värde i taget och fortlöpande hålla reda på den information som behövs för att till slut kunna ange minsta värde, största värde och medelvärde.

Laborationen tränar därför inte bara på att få fram tre svar. Det centrala är att förstå hur en loop kan bearbeta en dataström steg för steg.

## Lärandemål
Efter laborationen ska du kunna:
- läsa en följd av heltal från standard input,
- använda en loop för att behandla ett okänt antal värden,
- använda selektion för att uppdatera minsta och största observerade värde,
- hålla reda på summa och antal utan att lagra hela datamängden,
- beräkna medelvärde med korrekt typkonvertering,
- använda omdirigering för att låta en fil bli programmets standard input,
- konstruera små testfall där förväntat resultat kan beräknas för hand,
- använda Git för att dokumentera utvecklingen i meningsfulla steg.

## Förutsättningar och indata
Indata består av **minst ett heltal**. Heltalen är separerade med whitespace, till exempel mellanslag eller radbrytningar.

Du behöver i denna laboration **inte** hantera:
- tom indata,
- bokstäver eller annan felaktigt formaterad indata,
- felhantering av filer.

 Laborationens fokus är iteration, selektion och aritmetik.

## Uppgift
Skapa ett fristående C++-program som läser ett godtyckligt antal heltal från standard input. När EOF nås ska programmet skriva ut:

1. minsta värdet,
2. största värdet,
3. medelvärdet.

Medelvärdet ska beräknas som ett flyttal så att decimaler inte förloras.

## Obligatoriska begränsningar
Programmet ska behandla **ett inläst värde i taget**.

Du får därför inte:
- läsa in samtliga värden i en samling,
- använda `std::min`, `std::max`, `std::min_element` eller `std::max_element` för lösningen,
- använda `INT_MIN`, `INT_MAX` eller andra extremvärden för att initiera minimum och maximum.

Programmet ska själv hålla reda på den information som krävs under genomläsningen.

### Fundera innan du kodar
Vilken information måste finnas kvar efter att ett värde har behandlats för att nästa värde ska kunna behandlas korrekt?

## Standard input och EOF
Programmet ska läsa med vanlig standard input, exempelvis `std::cin`. Det ska alltså inte öppna `values.txt` med filhantering.

Vid interaktiv körning kan du skriva heltal i terminalen. På Linux/macOS avslutas inmatningen normalt genom att signalera EOF med `Ctrl+D`.

När programmet är färdigt ska samma program kunna läsa den medföljande filen genom omdirigering:

```bash
./minmax < data/values.txt
```

Programmet känner då inte till filnamnet. Shell-miljön kopplar filens innehåll till programmets standard input.

## Den medföljande values.txt
`student_arbete/data/values.txt` är laborationens större datamängd och innehåller många heltal, inklusive positiva värden, negativa värden och nollor.

Den stora filen är främst avsedd för slutlig körning. Under utvecklingen bör du börja med små egna talserier där du själv kan räkna ut rätt svar.

## Rekommenderad arbetsgång

### Steg 1 - Läs ett första värde
Eftersom indatat ska vara minst ett heltal, kan det första värdet läsas separat. Fundera på hur detta värde kan hjälpa dig att initiera minimum och maximum utan extremvärden.

### Steg 2 - Skapa inläsningsloopen
Läs därefter ett värde i taget tills EOF nås.

### Steg 3 - Uppdatera programmets tillstånd
För varje nytt värde behöver relevant information uppdateras. Fundera på vilka variabler som krävs.

### Steg 4 - Beräkna medelvärdet
Kontrollera särskilt att heltalsdivision inte förstör decimaldelen.

### Steg 5 - Testa med små, handberäknade fall
Skapa minst tre egna testfall. Välj dem så att de tillsammans provar olika delar av algoritmen. Dokumentera dem i `student_arbete/tester/testprotokoll.md`.

### Steg 6 - Kör med values.txt
När de små testerna fungerar kör du programmet mot den medföljande stora datamängden:

```bash
./minmax < data/values.txt
```

Dokumentera resultatet i testprotokollet.

### Steg 7 - Granska och dokumentera
Kontrollera koden, granska din Git-historik före redovisningen.

## Byggning
Från katalogen `student_arbete`:

```bash
make
```

Rensa den skapade körbara filen med:

```bash
make clean
```

## Testning
Dokumentera **minst tre små egna testfall**. De ska vara så små att du själv kan räkna ut förväntat minimum, maximum och medelvärde utan att lita på programmet.

Bra teststrategi kan exempelvis innebära att testa olika ordningsföljder, negativa värden eller upprepade värden. Det viktiga är att kunna motivera vad varje test kontrollerar.

Därefter görs en separat slutlig körning med `values.txt`.

## Git-arbetsflöde
Allt arbete som du producerar för lösningen ska ligga i `student_arbete/`.

Du ska göra minst **tre meningsfulla commits** under utvecklingen. En meningsfull commit representerar ett begripligt steg i arbetet.

Exempel på en rimlig utvecklingshistorik:

```text
Implement input loop and counting
Add min and max tracking
Calculate average and document tests
```

Undvik commit-meddelanden som:

```text
test
fix
klart
final
```

Använd Git under arbetets gång, till exempel:

```bash
git status
git diff
git add student_arbete/
git commit -m "Add min and max tracking"
git log --oneline
git push
```

## Muntlig redovisning
Vid redovisningen ska du kunna:
- bygga programmet från terminalen,
- köra programmet med omdirigering från `values.txt`,
- förklara hur inläsningsloopen avslutas,
- förklara varför alla tal inte behöver lagras,
- förklara hur minimum och maximum initieras,
- förklara hur minimum, maximum, summa och antal förändras när ett nytt värde läses,
- förklara varför medelvärdesberäkningen ger decimaler,
- kunna visa och motivera dina små testfall,
- visa `git log --oneline` och beskriva minst tre utvecklingssteg.

## Krav för godkänt
- Programmet uppfyller kraven för uppgiften.
- Ett värde behandlas i taget och hela datamängden lagras inte.
- De förbjudna färdiga min/max-lösningarna och sentinelvärdena används inte.
- Minimum, maximum och medelvärde beräknas korrekt.
- Programmet kan byggas och köras från terminalen.
- Git-historiken innehåller minst tre meningsfulla commits.
- Studenten kan muntligt förklara sin egen lösning.
