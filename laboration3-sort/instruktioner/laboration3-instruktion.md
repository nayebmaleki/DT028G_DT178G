# Laboration 3 - Sorteringskontroll och merge

## Tema

 Algoritmläsning, funktioner, headerfiler, flera källfiler, fil-I/O, testning och Git.

## Syfte

I denna laboration ska du inte uppfinna algoritmerna från början. Du ska **läsa två givna algoritmer i pseudokod, förstå varför de fungerar och översätta dem till C++**.

## Lärandemål

Efter laborationen ska du kunna:

- följa pseudokod steg för steg,
- översätta pseudokod till C++,
- förklara vilket tillstånd en algoritm behöver bevara,
- använda funktioner, headerfiler och flera `.cpp`-filer,
- avgöra om en fil är sorterad utan att lagra hela filen,
- merge:a två sorterade filer utan efterföljande sortering,
- testa algoritmer med små handkontrollerbara data,
- dokumentera utvecklingen med Git.

## Indata

I `student_arbete/data/` finns originalfilerna `A`, `A1` och `B`. Två är sorterade i icke-avtagande ordning och en innehåller ett ordningsbrott. Din egen `is_sorted` ska avgöra vilka.

Filerna innehåller minst ett korrekt formaterat heltal. Dubbletter är tillåtna. Icke-avtagande ordning innebär att nästa värde får vara lika stort, men inte mindre än föregående.

---

# Del 1 - is_sorted

Deklarationen finns i `include/is_sorted.h`. Implementera funktionen i `src/is_sorted.cpp`.

## Algoritm 1 - pseudokod

```text
ALGORITHM is_sorted(filename)

    open filename for reading

    read first value into previous

    WHILE another value can be read into current

        IF current < previous
            RETURN false
        END IF

        previous = current

    END WHILE

    RETURN true
```

## Frågor att förstå innan du kodar

1. Vad representerar `previous` och `current`?
2. Varför behövs inte alla tidigare värden?
3. Varför bevisar `current < previous` att filen är osorterad?
4. Varför får funktionen returnera direkt då?
5. Varför är lika värden tillåtna?
6. Varför läses första värdet före loopen?

## Krav

- Översätt pseudokoden till C++ och bevara dess grundstruktur.
- Läs ett värde i taget.
- Använd inte `vector`, array eller annan samling för hela filen.
- Använd inte en färdig sorteringsfunktion.
- Kontrollera att filen kan öppnas.

---

# Del 2 - merge_sorted

Deklarationen finns i `include/merge_sorted.h`. Implementera funktionen i `src/merge_sorted.cpp`.

## Algoritm 2 - pseudokod

```text
ALGORITHM merge_sorted(file1, file2, output)

    open file1 for reading
    open file2 for reading
    open output for writing

    read one value from file1 into a
    read one value from file2 into b

    WHILE file1 AND file2 both have a current value

        IF a <= b
            write a to output
            read next value from file1 into a
        ELSE
            write b to output
            read next value from file2 into b
        END IF

    END WHILE

    WHILE file1 still has a current value
        write a to output
        read next value from file1 into a
    END WHILE

    WHILE file2 still has a current value
        write b to output
        read next value from file2 into b
    END WHILE
```

## Frågor att förstå innan du kodar

1. Vad representerar `a` och `b`?
2. Varför räcker det att jämföra de två aktuella värdena?
3. Varför kan det mindre värdet skrivas direkt?
4. Varför måste båda infilerna redan vara sorterade?
5. Vad händer med det värde som inte skrivs?
6. Vad händer när `a == b`?
7. Varför försvinner inga dubbletter?
8. Varför behövs de två sista looparna?
9. Vad vet vi om resterande värden när ena filen når EOF?

## Centralt krav

Du får inte först slå ihop filerna och sedan sortera resultatet. Resultatet ska bli sorterat genom själva merge-algoritmen. Hela filerna får inte lagras i minnet.

---

# Del 3 - main.cpp

Demonstrationsprogrammet ska:

1. kontrollera A, A1 och B med `is_sorted`,
2. skriva vilka filer som är sorterade,
3. identifiera de två sorterade filerna,
4. merge:a endast sorterad indata,
5. skapa `data/merged.txt`,
6. kontrollera `merged.txt` med `is_sorted`,
7. skriva tydliga resultat i terminalen.

`merged.txt` är genererad utdata.

## Bygg och kör

Från `student_arbete`:

```bash
make
./sort_demo
```

## Testning

Skapa först små egna testfiler där pseudokoden kan följas för hand. Dokumentera minst tre tester i `tester/testprotokoll.md`. Testerna ska tillsammans prova sorterad/osorterad data, dubbletter, merge och fallet där ena merge-filen tar slut först.

Kör därefter slutdemonstrationen med originalfilerna A/A1/B.

## Muntlig redovisning

Du ska kunna läsa pseudokoden, förklara varje central del och peka ut motsvarande C++-kod. Du ska också kunna motivera `IF current < previous`, `IF a <= b`, de två avslutande merge-looparna, dubbletthantering samt förklara modulariseringen och din Git-historik.

## Krav för godkänt

- båda pseudokodsalgoritmerna kan förklaras,
- C++-implementationerna motsvarar pseudokodens grundstruktur,
- funktionerna ligger i separata `.cpp`-filer med headers,
- inga hela filer lagras i samlingar,
- merge-resultatet sorteras inte i efterhand,
- dubbletter bevaras,
- originalfilerna A/A1/B används,
- testprotokoll är ifyllda,
- minst tre meningsfulla Git-commits finns,
- studenten kan muntligt koppla pseudokod till implementation.
