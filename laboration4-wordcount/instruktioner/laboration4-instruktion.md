# Laboration 4 - Ordfrekvens i text

## Tema

Textbearbetning, `std::string`, `std::map`, `std::vector`, standardalgoritmer, sortering, funktioner, testning och Git.

## Lärandemål

Efter laborationen ska du kunna:

- dela upp ett problem i flera funktioner,
- normalisera text till ord på ett konsekvent sätt,
- använda `std::map<std::string, int>` för frekvensräkning,
- omvandla map-data till en struktur som kan sorteras efter frekvens,
- använda `std::sort` med en egen jämförelseregel,
- jämföra en C++-lösning med en UNIX-pipeline,
- skapa små testfall med känd förväntad utdata,
- dokumentera arbetet med Git.

## Uppgift

Skapa ett programmet som läser `data/hitchhikersguide.txt` och skriver ut de `n` vanligaste orden till terminalen, mest förekommande först. `n` ska enkelt kunna ändras i programmet.

För denna version använder vi:

```cpp
constexpr std::size_t TOP_N = 50;
```

- **const** betyder att ett värde inte får ändras efter initiering.
- **constexpr** betyder att värdet kan beräknas redan vid kompilering och är samtidigt const.

## Referens: UNIX-pipelinen

I ett UNIX-likt system kan nedanstående lösningsidé användas:

```bash
n=50
cat hitchhikersguide.txt | tr -cs A-Za-z '\n' | tr A-Z a-z | \
    sort | uniq -c | sort -rn | head -n $n
```

Du behöver inte använda denna pipeline för att lösa uppgiften. Din C++-lösning ska genomföra motsvarande problem i C++.

## Indata och orddefinition

För att tester ska bli entydiga definierar vi ett ord som en **sammanhängande sekvens av ASCII-bokstäver `A-Z` eller `a-z`**.

Det innebär exempelvis:

```text
Hello, HELLO! hello
```

blir tre förekomster av:

```text
hello
```

Apostrofer, bindestreck, siffror och annan interpunktion fungerar som avgränsare. Alla ord omvandlas till gemener innan de räknas.

## Rekommenderad problemlösning

Arbeta i denna ordning:

```text
textfil
  |
  v
normalisera tecken till ord
  |
  v
räkna orden i std::map
  |
  v
kopiera ord + antal till std::vector
  |
  v
sortera efter antal
  |
  v
skriv de n första
```

# Del 1 - Normalisering och frekvensräkning

Implementera en funktion i `src/word_count.cpp` som läser en fil och returnerar:

```cpp
std::map<std::string, int>
```

med ett frekvensvärde för varje ord.

Du ska använda orddefinitionen ovan. En praktisk strategi är att läsa ett tecken i taget:

- bokstav: lägg gemen bokstav till aktuellt ord,
- annat tecken: avsluta aktuellt ord om det inte är tomt,
- efter EOF: glöm inte ett eventuellt sista ord.

## Frågor att kunna besvara

1. Varför passar en `map` för att räkna förekomster?
2. Vad händer när `counts[word]` används för ett ord som ännu inte finns?
3. Varför normaliseras stora och små bokstäver?
4. Varför måste ett sista ord behandlas även när filen slutar utan skiljetecken?

# Del 2 - Rangordna orden

En `std::map` är ordnad efter **nyckeln**, alltså ordet, inte efter frekvensen. För att hitta de vanligaste orden ska du skapa en `std::vector` med poster som innehåller både ord och antal och därefter sortera vektorn.

I startprojektet finns typen:

```cpp
struct WordFrequency {
    std::string word;
    int count;
};
```

Sorteringsregeln ska vara:

1. högre `count` först,
2. om två ord har samma `count`, sortera alfabetiskt efter `word`.

Den andra regeln gör resultatet deterministiskt och testbart.

## Frågor att kunna besvara

1. Varför räcker inte `map`-ordningen?
2. Varför är en `vector` praktisk före `std::sort`?
3. Vad betyder en egen jämförelsefunktion/lambda för `std::sort`?
4. Varför behöver vi bestämma vad som händer vid lika frekvens?

# Del 3 - Top N och main

I `src/main.cpp` ska:

- `TOP_N` vara enkelt att ändra,
- den riktiga textfilen läsas,
- de vanligaste orden skrivas som `antal ord`, en post per rad,
- programmet fungera även om det finns färre än `TOP_N` unika ord.

Exempel på **format**, inte på resultat från den riktiga boken:

```text
5 the
3 answer
2 galaxy
```

# Testning

Skapa först små textfiler där du kan räkna för hand. `tester/testprotokoll.md` ska dokumentera minst tre tester:

1. **Normalisering:** versaler och interpunktion.
2. **Frekvens och tie-break:** flera ord med samma frekvens.
3. **Top N:** fler unika ord än det `n` som skrivs ut.

Kör därefter med `hitchhikersguide.txt` som sluttest. Den stora textfilen ska alltså inte vara ditt första felsökningstest.

# Byggning

Från `student_arbete`:

```bash
make
./wordcount
```

# Git

Följ `gemensamma-instruktioner/arbetsgang_och_git_laborationer.md`. Minst tre meningsfulla commits krävs.

# Muntlig redovisning

Du ska kunna:

- förklara varför `map` används för räkning,
- förklara varför resultaten flyttas till en `vector`,
- förklara jämförelseregeln i `std::sort`,
- förklara hur `TOP_N` begränsar utskriften,
- visa små tester och Git-historik.

# Krav för godkänt

- text normaliseras enligt laborationens orddefinition,
- frekvenser räknas korrekt,
- `std::map`, `std::vector` och `std::sort` används meningsfullt,
- högst `TOP_N` poster skrivs, högst frekvens först,
- lika frekvens bryts alfabetiskt,
- lösningen är uppdelad i funktioner,
- minst tre små tester och en slutkörning dokumenteras,
- minst tre meningsfulla Git-commits finns,
- studenten kan förklara lösningen muntligt.
