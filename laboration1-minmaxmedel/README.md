# Struktur för Laboration 1

Detta dokument visar katalogstrukturen för **Laboration 1** i kursrepositoryt `DT028G_DT178G`.

## Katalogstruktur

```text
laboration1-minmaxmedel/
├── README.md
│
├── instruktioner/
│   └── laboration1-instruktion.md
│
└── student_arbete/
    ├── README.md
    ├── Makefile
    │
    ├── src/
    │   └── main.cpp
    │
    ├── data/
    │   └── values.txt
    │
    └── tester/
        └── testprotokoll.md
```

## Katalogernas och filernas roller

### `README.md`

Denna fil.

### `instruktioner/`

Innehåller instruktionen som endast gäller **laboration 1**:

```text
instruktioner/laboration1-instruktion.md
```

### `student_arbete/`

Detta är studentens arbetskatalog. Studenten ska gå till denna katalog innan programmet byggs, körs och testas.

```bash
cd laboration1/student_arbete
```

### `student_arbete/src/`

Innehåller laborationens C++-källkod:

```text
src/main.cpp
```

### `student_arbete/data/`

Innehåller laborationens datafiler:

```text
data/values.txt
```

Om programmet ska läsa indata från fil kan det exempelvis köras med:

```bash
./program < data/values.txt
```

### `student_arbete/tester/`

Innehåller studentens testprotokoll:

```text
tester/testprotokoll.md
```

Se exemplet på testprotokoll som finns i repositoryt:

```text
../../gemensamma-instruktioner/testprotokoll_exempel.md
```

### `student_arbete/Makefile`

Beskriver hur laborationens program byggs, körs och rensas. Kommandon som `make`, `make run` och `make clean` körs från `student_arbete/`.

## Gemensamma instruktioner

Instruktioner som gäller för samtliga laborationer finns i:

```text
DT028G_DT178G/gemensamma-instruktioner/
```

Där kan exempelvis följande finnas:

```text
gemensamma-instruktioner/
├── arbetsgang_och_git_laborationer.md
└── testprotokoll_exempel.md
```

## Rekommenderad arbetsgång

1. Läs `laboration1-instruktion.md`.
2. Läs relevanta dokument i `gemensamma-instruktioner/`.
3. Gå till `laboration1-minmaxmedel/student_arbete/`.
4. Arbeta med ett mindre utvecklingssteg i taget.
5. Bygg och kör programmet.
6. Genomför och dokumentera relevanta tester.
7. Skapa meningsfulla commits under arbetets gång (minst 3).
8. Pusha regelbundet till ditt privata repository.
