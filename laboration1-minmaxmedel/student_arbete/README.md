# Studentens arbetsyta

Allt arbete som hör till din lösning ska ligga i denna katalog.

```text
student_arbete/
├── Makefile
├── README.md
├── src/
│   └── main.cpp
├── data/
│   └── values.txt
└── tester/
    └── testprotokoll.md
```

## Bygg

```bash
make
```

## Kör med egen interaktiv indata

```bash
./minmax
```

Indata innehåller minst ett heltal. På Linux/macOS avslutas den interaktiva inmatningen normalt med `Ctrl+D` för att signalera EOF.

## Kör med laborationens datafil

```bash
./minmax < data/values.txt
```

Börja inte din testning med den stora filen. Använd först små testfall där du själv kan beräkna rätt svar.
