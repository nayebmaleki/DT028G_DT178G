# Arbetsgång och Git för laborationer

Det här dokumentet beskriver den gemensamma arbetsgång som ska användas i kursens laborationer. Syftet är att du ska arbeta systematiskt, testa lösningen stegvis och skapa en tydlig utvecklingshistorik med Git.

> **Grundprincip:** Arbeta med en liten, sammanhängande del i taget. Testa delen, granska ändringarna, skapa en meningsfull commit och pusha regelbundet till GitHub.

---

## 1. Börja med laborationsinstruktionen och projektstrukturen

Innan du börjar skriva eller ändra kod ska du:

1. läsa `laborations_instruktion.md` i sin helhet,
2. identifiera laborationens krav och delproblem,
3. studera strukturbilden i `README.md` för att se var olika filer och kataloger finns,
4. kontrollera var din kod och testdokumentation ska sparas,
5. kontrollera hur programmet ska byggas, köras och testas.

`README.md` ger en översikt över laborationens katalogstruktur. De detaljerade kraven och arbetsinstruktionerna finns i `laborationX-instruktion.md`.

X är numret till laborationen. Till exempel: `laboration1-instruktion.md`

Behåll den angivna katalogstrukturen. Kod, tester och annan dokumentation som du själv producerar ska placeras i de kataloger som anges i laborationsinstruktionen.

---

## 2. Kontrollera startläget

Innan du börjar utveckla lösningen ska du kontrollera att startprojektet fungerar enligt instruktionen.

Gå till den arbetskatalog som anges i strukturbilden och laborationsinstruktionen. Om projektet använder en `Makefile` kan startkontrollen exempelvis göras med:

```bash
make
```

Använd det bygg-, kör- och testkommando som anges i `laborationX-instruktion.md`.

Kontrollera också Git-repositoryts aktuella tillstånd:

```bash
git status
```

Startkoden ska kunna byggas eller köras innan du börjar göra egna ändringar. Om startprojektet inte fungerar ska du först kontrollera att du:

- befinner dig i rätt katalog,
- har följt installationsanvisningarna,
- använder rätt kommando,
- inte oavsiktligt har ändrat startfilerna.

---

## 3. Dela upp laborationen i mindre steg

Laborationen ska inte lösas som en enda stor ändring. Dela i stället upp arbetet i mindre, begripliga delproblem.

En möjlig progression är att:

1. få programmets grundstruktur att fungera,
2. implementera en första avgränsad funktion,
3. testa funktionen med enkla indata,
4. lägga till nästa del av lösningen,
5. testa hur delarna fungerar tillsammans,
6. hantera relevanta gränsfall och specialfall,
7. genomföra och dokumentera slutliga tester.

Den exakta progressionen beror på laborationen. Varje steg ska vara tillräckligt litet för att du ska kunna förstå vad som har ändrats och kontrollera om ändringen fungerar.

---

## 4. Använd det återkommande arbetsflödet

För varje mindre delproblem använder du följande arbetscykel:

```text
Läs det aktuella kravet
          ↓
Implementera en mindre del
          ↓
Bygg eller kör programmet
          ↓
Testa resultatet
          ↓
Granska ändringarna med Git
          ↓
Skapa en meningsfull commit
          ↓
Pusha till GitHub
          ↓
Fortsätt med nästa delproblem
```

Om programmet inte fungerar som förväntat går du tillbaka till koden, gör en mindre korrigering och testar igen.

Skapa inte en commit enbart för att koden har ändrats. En commit ska representera ett begripligt och fungerande utvecklingssteg.

---

## 5. Testa med små och oberoende testfall

Börja med små testfall där du själv kan beräkna det förväntade resultatet. Då kan du jämföra programmets resultat med ett resultat som har bestämts oberoende av programmet.

Det förväntade resultatet ska alltså inte tas fram genom samma program som du försöker kontrollera. Detta arbetssätt förbereder dig för automatiserad testning med testramverk som exempelvis `unittest` eller `pytest` i Python.

Dokumentera minst tre egna testfall, om laborationsinstruktionen inte anger ett högre antal. Välj testfallen så att de tillsammans undersöker olika egenskaper hos lösningen, exempelvis:

- ett **normalfall** med vanliga indata,
- ett **gränsfall** nära problemets tillåtna gränser,
- ett **specialfall eller felfall** som kan avslöja brister i lösningen.

För varje dokumenterat test ska du ange:

- testets syfte,
- vilka indata som används,
- vilket resultat du förväntar dig,
- vilket resultat programmet faktiskt ger,
- om testet är godkänt eller inte.

Spara testdokumentationen på den plats som anges i `laborations_instruktion.md`. Använd strukturbilden i `README.md` för att hitta rätt katalog.

> **Viktigt:** Använd inte ett stort slutligt dataunderlag för att avgöra om den första versionen av lösningen är korrekt. Börja smått, där du själv kan kontrollera svaret.

---

## 6. Granska ändringarna före varje commit

Kontrollera arbetskatalogen:

```bash
git status
```

Granska vad som har ändrats:

```bash
git diff
```

Fråga dig själv:

- Hör alla ändringar till samma logiska utvecklingssteg?
- Finns det tillfälliga filer eller byggfiler som inte ska versionshanteras?
- Har jag testat ändringen?
- Kan jag förklara vad ändringen gör och varför den behövs?

Lägg sedan till de filer som hör till utvecklingssteget. Exempel:

```bash
git add student_arbete/
```

Kontrollera på nytt vad som kommer att ingå:

```bash
git status
```

Granska de ändringar som har lagts till i stagingområdet:

```bash
git diff --staged
```

---

## 7. Skapa meningsfulla commits

Skapa en commit när ett mindre, sammanhängande steg fungerar:

```bash
git commit -m "Implementerar validering av indata"
```

Ett bra commit-meddelande beskriver vad som förändrades. Exempel:

```text
Implementerar programmets inläsning
Lägger till beräkning av minsta och största värde
Hanterar tom indata
Dokumenterar tester för gränsfall
Rättar validering av menyval
```

Undvik otydliga commit-meddelanden som:

```text
fix
test
ändring
klart
final
```

Sådana meddelanden beskriver inte vad som har förändrats och gör utvecklingshistoriken svår att förstå.

Gör minst tre meningsfulla commits under arbetet, om `laborations_instruktion.md` inte anger ett högre krav. Tre commits är ett minimikrav, inte ett mål. En laboration kan naturligt kräva fler utvecklingssteg.

---

## 8. Pusha regelbundet

Skicka dina commits till ditt privata repository på GitHub:

```bash
git push
```

Pusha regelbundet under arbetets gång, inte enbart när laborationen är färdig. Då finns arbetet sparat på GitHub och utvecklingshistoriken blir tillgänglig inför redovisningen.

Kom ihåg skillnaden:

- `git add` väljer vilka ändringar som ska ingå i nästa commit,
- `git commit` sparar utvecklingssteget i den lokala Git-historiken,
- `git push` skickar lokala commits till GitHub.

---

## 9. Genomför laborationens slutliga test

När de mindre testerna fungerar genomför du laborationens slutliga test enligt instruktionen. Det kan exempelvis innebära att du:

- kör programmet med ett större dataunderlag,
- kör automatiska tester,
- kontrollerar flera sammanhängande funktioner,
- gör en fullständig byggning av projektet,
- dokumenterar slutresultatet i ett testprotokoll.

Använd alltid de kommandon, datafiler och krav som anges i `laborations_instruktion.md`. Använd strukturbilden i `README.md` för att hitta rätt filer och kataloger.

Om sluttestet avslöjar ett fel ska du återgå till det stegvisa arbetsflödet:

1. avgränsa felet,
2. gör en mindre korrigering,
3. bygg eller kör programmet igen,
4. testa korrigeringen,
5. granska ändringen,
6. skapa en ny commit,
7. pusha till GitHub.

---

## 10. Kontrollera arbetet före redovisningen

Bygg eller kör programmet från ett rent och känt utgångsläge enligt `laborations_instruktion.md`.

Om projektet använder `make` kan kontrollen exempelvis börja med:

```bash
make clean
make
```

Kontrollera därefter repositoryt:

```bash
git status
git log --oneline
git remote -v
```

Före redovisningen ska du säkerställa att:

- programmet kan byggas eller köras enligt instruktionen,
- de dokumenterade testerna kan genomföras och förklaras,
- relevanta normalfall, gränsfall och specialfall har testats,
- arbetskatalogen inte innehåller oavsiktliga ändringar,
- commit-historiken visar en stegvis utveckling,
- alla relevanta commits har pushats till GitHub,
- inga byggfiler, temporära filer eller hemligheter har committats.

---

## 11. Förbered din muntliga förklaring

Vid redovisningen ska du kunna förklara lösningen utan att enbart läsa koden rad för rad.

Förbered dig på att beskriva:

- hur du delade upp problemet,
- hur algoritmen eller lösningen fungerar,
- vilka antaganden lösningen bygger på,
- hur programmets tillstånd förändras under körningen,
- varför dina testfall är relevanta,
- vad några av dina commits tillförde,
- vilka fel eller svårigheter du mötte och hur du hanterade dem.

Visa utvecklingshistoriken med:

```bash
git log --oneline
```

En viss commit kan granskas med:

```bash
git show <commit-id>
```

---

## 12. Märk redovisningsversionen om instruktionen kräver det

Vissa laborationer kan kräva att redovisningsversionen märks med en Git-tagg. Gör detta endast när det anges i `laborations_instruktion.md`.

Exempel:

```bash
git tag presentation
git push origin presentation
git rev-parse presentation
```

Kommandona:

- skapar taggen `presentation`,
- skickar taggen till GitHub,
- visar vilket commit-ID taggen pekar på.

Lämna repositorylänk, tagg, commit-ID eller annan information i Canvas enligt den aktuella laborationsinstruktionen och angiven deadline.

---

# Kort Git-guide

## Kontrollera arbetskatalogen

```bash
git status
```

## Se dina ändringar

```bash
git diff
```

## Välj ändringar

```bash
git add <fil-eller-katalog>
```

## Granska valda ändringar

```bash
git diff --staged
```

## Skapa en commit

```bash
git commit -m "Beskriv det fungerande utvecklingssteget"
```

## Se historiken

```bash
git log --oneline
```

## Pusha arbetet

```bash
git push
```

---

# Checklista

## När du börjar

- [ ] Jag har läst `laborationX-instruktion.md` i sin helhet.
- [ ] Jag har studerat strukturbilden i `README.md`.
- [ ] Jag förstår vilka krav och delproblem laborationen innehåller.
- [ ] Jag vet var min kod och testdokumentation ska sparas.
- [ ] Jag har kontrollerat hur programmet ska byggas, köras och testas.
- [ ] Jag har kontrollerat repositoryt med `git status`.

## Under arbetet

- [ ] Jag arbetar med ett mindre delproblem i taget.
- [ ] Jag testar varje del innan jag fortsätter.
- [ ] Jag börjar med små testfall där jag själv kan bestämma rätt resultat.
- [ ] Jag dokumenterar minst tre varierade testfall.
- [ ] Jag granskar ändringarna med `git status` och `git diff`.
- [ ] Jag kontrollerar stagingområdet med `git diff --staged`.
- [ ] Jag skapar meningsfulla commits.
- [ ] Jag pushar regelbundet till GitHub.

## Inför redovisningen

- [ ] Programmet går att bygga eller köra enligt instruktionen.
- [ ] Alla relevanta tester fungerar och är dokumenterade.
- [ ] Jag kan förklara lösningen och testfallen.
- [ ] Commit-historiken visar en stegvis utveckling.
- [ ] Alla relevanta commits är pushade.
- [ ] Jag har skapat en tagg om laborationsinstruktionen kräver det.
- [ ] Jag har lämnat rätt information i Canvas.
