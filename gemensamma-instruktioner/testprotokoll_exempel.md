# Testprotokoll - exempel och förklaring

Det här är en **exempelfil** som visar vad som menas med normalfall, gränsfall och specialfall.

Exemplen nedan utgår från ett program som läser heltal och redovisar:

- antal värden
- summa
- minsta värde
- största värde
- medelvärde

Om din laboration beräknar något annat ska du behålla testprincipen men anpassa indata och förväntat resultat till uppgiften.

> Skapa eller fyll i `tester/testprotokoll.md` för din egen laboration. Ändra inte nödvändigtvis denna exempelfil.

## Från manuella tester till automatiserad testning

I större C++-program genomförs många sådana kontroller med ett **testramverk för C++**. Ett testramverk kan köra testfall automatiskt, jämföra programmets faktiska resultat med det förväntade resultatet och rapportera vilka tester som blev godkända eller underkända.

I den här laborationen genomförs testerna manuellt och dokumenteras i ett testprotokoll. Syftet är att du först ska utveckla förståelse för **vad som behöver testas och varför**:

- vilka normala indata programmet ska klara
- vilka gränser som är viktiga att kontrollera
- vilka specialfall som kan avslöja fel i algoritmen
- vilket resultat som förväntas för ett visst testfall
- hur det faktiska resultatet jämförs med det förväntade

Ett automatiserat test i C++ bygger på samma tankesätt. Skillnaden är att indata, förväntat resultat, körning och jämförelse senare uttrycks i testkod och hanteras av ett testramverk, i stället för att genomföras och dokumenteras helt för hand.

Den manuella testningen i detta protokoll är därför en förberedelse inför framtida arbete med automatiserade tester i C++. När du senare använder ett testramverk kommer du redan att kunna formulera relevanta testfall, eftersom du har tränat på sambandet:

```text
syfte → indata → förväntat resultat → faktiskt resultat → godkänt eller underkänt
```

> Ett testramverk kan automatisera körningen, jämförelsen och rapporteringen. Testramverket kan däremot inte själv avgöra vilka testfall som är viktiga. Det är fortfarande programmeraren som måste välja relevanta normalfall, gränsfall och specialfall.

## Så genomför du ett test

För varje test:

1. bestäm vad testet ska kontrollera
2. välj en liten mängd indata
3. beräkna det förväntade resultatet för hand
4. kör programmet
5. skriv in det faktiska resultatet
6. jämför resultaten och markera testet som godkänt eller underkänt

---

## Test 1: Normalfall

Ett **normalfall** innehåller vanliga, giltiga värden och kontrollerar programmets huvudsakliga funktion.

### Syfte

Kontrollera att programmet behandlar flera vanliga positiva heltal korrekt.

### Indata

```text
4
8
2
6
```

### Förväntat resultat

Beräkning för hand:

```text
Antal: 4
Summa: 4 + 8 + 2 + 6 = 20
Minsta värde: 2
Största värde: 8
Medelvärde: 20 / 4 = 5
```

Förväntad programutskrift, anpassad till programmets format:

```text
Antal: 4
Summa: 20
Minsta värde: 2
Största värde: 8
Medelvärde: 5
```

### Faktiskt resultat

```text
Fylls i efter körningen.
```

### Godkänt

- [ ] Ja
- [ ] Nej

### Kommentar

Skriv en kommentar om det faktiska resultatet skiljer sig från det förväntade.

---

## Test 2: Gränsfall - endast ett värde

Ett **gränsfall** ligger vid en viktig gräns i uppgiften. Här testas det minsta meningsfulla antalet värden: ett enda värde.

### Syfte

Kontrollera att programmet fungerar när indata bara innehåller ett värde.

### Indata

```text
7
```

### Förväntat resultat

```text
Antal: 1
Summa: 7
Minsta värde: 7
Största värde: 7
Medelvärde: 7
```

Det enda värdet måste samtidigt bli summa, minsta värde, största värde och medelvärde.

### Faktiskt resultat

```text
Fylls i efter körningen.
```

### Godkänt

- [ ] Ja
- [ ] Nej

### Kommentar

Kontrollera särskilt att programmet inte förutsätter att flera värden alltid finns.

---

## Test 3: Specialfall - alla värden är lika

Ett **specialfall** är giltig indata med en särskild egenskap som kan avslöja fel i algoritmen.

### Syfte

Kontrollera att programmet fungerar när alla värden är identiska.

### Indata

```text
5
5
5
5
```

### Förväntat resultat

```text
Antal: 4
Summa: 20
Minsta värde: 5
Största värde: 5
Medelvärde: 5
```

### Faktiskt resultat

```text
Fylls i efter körningen.
```

### Godkänt

- [ ] Ja
- [ ] Nej

### Kommentar

Kontrollera särskilt att både minsta och största värde blir 5.

---

## Alternativa specialfall

Välj bara sådana fall som är giltiga enligt laborationens krav.

### Negativa och positiva värden

Om negativa värden är tillåtna:

```text
-5
10
-3
2
```

Förväntat:

```text
Antal: 4
Summa: 4
Minsta värde: -5
Största värde: 10
Medelvärde: 1
```

### Alla värden är noll

```text
0
0
0
```

Förväntat:

```text
Antal: 3
Summa: 0
Minsta värde: 0
Största värde: 0
Medelvärde: 0
```

### Värden i fallande ordning

```text
9
6
3
1
```

Detta kan kontrollera att programmet hittar minsta och största värde oberoende av ordningen.

> Felaktig indata är inte automatiskt samma sak som ett specialfall. Testa exempelvis text i stället för heltal endast om laborationen kräver felhantering för sådan indata.

---

## Test 5: Eget testfall

### Syfte

Beskriv exakt vilken egenskap testet ska kontrollera.

### Indata

```text
Fyll i små värden som du kan kontrollera för hand.
```

### Förväntat resultat

```text
Räkna ut resultatet innan programmet körs.
```

### Faktiskt resultat

```text
Fylls i efter körningen.
```

### Godkänt

- [ ] Ja
- [ ] Nej

### Kommentar

Beskriv resultatet och eventuella rättningar.

---

## Slutlig körning med `values.txt`

Den stora datafilen används **efter** att de små testfallen har godkänts. Den ersätter inte de små testerna.

### Syfte

Kontrollera att det färdiga programmet kan läsa och behandla laborationens fullständiga dataunderlag.

### Kommando

Kör från katalogen `student_arbete`:

```bash
./program < data/values.txt
```

Om Makefile innehåller målet `values` kan du i stället köra:

```bash
make values
```

### Programmets resultat

```text
Klistra in eller sammanfatta programmets resultat här.
```

### Rimlighetskontroll

Beskriv kort varför resultatet verkar rimligt. Kontrollera exempelvis att:

- programmet läser hela filen
- programmet avslutas när filens slut nås
- antal behandlade värden verkar rimligt
- minsta och största värde ligger inom ett rimligt intervall
- programmet inte kraschar eller fastnar

### Godkänt

- [ ] Ja
- [ ] Nej

### Kommentar

```text
Skriv eventuella observationer här.
```

---

## Sammanfattning

De små testfallen verifierar algoritmen med resultat som kan beräknas för hand:

- **Normalfall:** vanliga giltiga värden
- **Gränsfall:** värden eller antal vid en viktig gräns
- **Specialfall:** giltig indata med en särskild egenskap

Körningen med `data/values.txt` är den avslutande körningen med laborationens större dataunderlag.
