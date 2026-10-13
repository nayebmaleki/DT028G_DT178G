# Laboration 2 - Fil-I/O och texthantering

## Tema

Fil-I/O, texthantering, strängar, strukturerad indata, validering, testning och Git.

## Bakgrund

Program behöver ofta läsa strukturerad text från filer, tolka informationen och skriva den i ett annat format. I denna laboration arbetar du med poster som består av tre rader: namn, personnummer och adress.

Till skillnad från laboration 1 ska programmet denna gång **självt öppna en indatafil och en utdatafil**. Omdirigering av standard input ska alltså inte användas som lösning.

## Lärandemål

Efter laborationen ska du kunna:

- öppna och kontrollera textfiler för läsning och skrivning i C++,
- läsa text radvis med `std::getline`,
- tolka en post med en känd struktur,
- dela upp en namnrad i förnamn och efternamn,
- extrahera en relevant siffra ur ett personnummer,
- använda villkor för att klassificera ett värde enligt en given regel,
- skriva transformerad text till en ny fil,
- testa filbaserad kod med små, handkontrollerade testfiler,
- dokumentera utvecklingen med meningsfulla Git-commits.

## Indata

Den medföljande filen finns här:

```text
student_arbete/data/names.txt
```

Varje post består av **exakt tre rader**:

```text
Förnamn Efternamn
ÅÅMMDDNNNN
Adressrad
```

Exempel från dataformatet:

```text
Måns Hansson
8510309159
Bössgränd 90, 373 02  RAMDALA
```

Den tillhandahållna `names.txt` innehåller många sådana poster. Den ska användas för den slutliga körningen. Under utvecklingen ska du skapa små egna testfiler.

## Indatakontrakt

Du får förutsätta att den fil som ska behandlas följer laborationens format:

- minst en fullständig post finns,
- varje post består av tre rader,
- namnradens första ord är förnamn och sista ord är efternamn,
- personnumret består av tio siffror i formatet `ÅÅMMDDNNNN`,
- adressen upptar exakt en rad.

Du behöver inte hantera trasiga eller ofullständiga poster i denna laboration. Däremot ska programmet kontrollera att indatafilen och utdatafilen kan öppnas.

## Uppgift

Laborationen genomförs i två delar. Gör del 1 färdig och testad innan du fortsätter med del 2.

### Del 1 - transformera poster

Programmet ska läsa posterna från `names.txt` och skriva dem till en **ny utdatafil** i följande form:

```text
Efternamn, Förnamn
Adressrad
```

Personnumret ska alltså läsas och användas som en del av posten, men ska inte skrivas ut i del 1.

För exemplet ovan blir utdata:

```text
Hansson, Måns
Bössgränd 90, 373 02  RAMDALA
```

### Del 2 - lägg till markering från personnumret

Utöka programmet så att det också skriver `[M]` eller `[K]` efter namnet.

I ett svenskt personnummer av formatet `ÅÅMMDDNNNN` är **den näst sista siffran**, alltså den tredje siffran i de fyra sista siffrorna, den siffra som används för juridisk könskodning. I denna laboration används följande tekniska regel:

- jämn siffra -> `[K]`
- udda siffra -> `[M]`

Programmet ska tillämpa denna regel på filens kodade uppgift. Laborationen handlar om strängbearbetning och villkorslogik, inte om att avgöra en persons kön utifrån namn eller andra egenskaper.

Exempel:

```text
Hansson, Måns [M]
Bössgränd 90, 373 02  RAMDALA
```

## Filhantering

Programmet ska använda filströmmar, exempelvis `std::ifstream` och `std::ofstream`.

Det ska alltså **inte** lösas med:

```bash
./parse < data/names.txt
```

Programmet ska själv öppna filen. Filnamnen kan anges tydligt i programmet enligt laborationens katalogstruktur, eller hanteras på annat enkelt sätt som läraren godkänner.

Utdata ska skrivas till exempelvis:

```text
student_arbete/data/output.txt
```

`output.txt` är genererad programutdata och ska inte versionshanteras.

## Rekommenderad arbetsgång

### Steg 1 - förstå en enda post

Skapa en liten egen testfil med en enda post. Läs de tre raderna och skriv tillfälligt ut dem så att du vet att filinläsningen fungerar.

### Steg 2 - lös del 1 för en post

Dela namninformationen och skriv posten i det nya formatet.

### Steg 3 - behandla flera poster

Lägg in behandlingen i en loop så att samma logik fungerar oavsett hur många fullständiga poster filen innehåller.

### Steg 4 - testa del 1

Använd små testfiler där du själv kan kontrollera exakt vilken utdata som ska skapas.

### Steg 5 - genomför del 2

Extrahera den relevanta siffran ur personnumret och använd dess paritet för att välja `[M]` eller `[K]`.

### Steg 6 - testa del 2

Använd minst två personnummer där den relevanta siffran har olika paritet så att båda grenarna i villkoret provas.

### Steg 7 - kör med names.txt

När små tester fungerar kör du programmet med den medföljande `names.txt` och granskar den skapade utdatafilen.

## Byggning

Från `student_arbete`:

```bash
make
```

Kör sedan:

```bash
./parse
```

## Testning

Dokumentera minst **tre små egna filbaserade tester** i `student_arbete/tester/testprotokoll.md`.

Testerna ska tillsammans kontrollera:

- korrekt omformatering av namn och adress,
- behandling av flera poster,
- både `[M]` och `[K]` i del 2.

Därefter görs en separat slutlig körning med den fullständiga `names.txt`.

## Git

Allt du själv producerar ska ligga i `student_arbete/`.

Minst tre meningsfulla commits krävs. En rimlig utvecklingshistorik kan vara:

```text
Read records and implement part 1 formatting
Process multiple records and add file checks
Add personal-number classification and tests
```

Gör minst tre commits under arbetets gång.

## Muntlig redovisning

Du ska kunna:

- bygga och köra programmet från terminalen,
- visa vilken fil programmet läser och vilken fil det skapar,
- förklara hur en tre-raderspost läses,
- förklara hur namn delas upp,
- visa slutkörningen med `names.txt`,
- kan visa `git log --oneline` och beskriva minst tre utvecklingssteg.

## Krav för godkänt

- Programmet använder faktisk filhantering.
- Indatafil och utdatafil kontrolleras när de öppnas.
- Alla fullständiga poster behandlas.
- Lösningen ger rätt namnordning och adress samt rätt `[M]`/`[K]` enligt den angivna personnummerregeln.
- Programmet fungerar med den medföljande `names.txt`.
- Git-historiken innehåller minst tre meningsfulla commits.
- Studenten kan muntligt förklara sin egen kod och algoritm.
