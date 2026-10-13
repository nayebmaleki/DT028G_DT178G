# Struktur för Laboration 3

Detta dokument visar katalogstrukturen för **Laboration 3** i kursrepositoryt `DT028G_DT178G`.

## Katalogstruktur

```text
laboration3-sort/
├── README
|
├── instruktioner/
│   └── laboration3-instruktion.md
│
└── student_arbete/
    ├── README.md
    ├── Makefile
    │
    ├── include/
    |   └── is_sorted.h
    |   └── merge_sorted.h
    |
    ├── src/
    │   └── main.cpp
    |   └── is_sorted.cpp
    |   └── merge_sorted.cpp
    │
    ├── data/
    │   └── A
    |   └── A1
    |   └── B
    │
    └── tester/
        └── testprotokoll.md
```

## Katalogernas och filernas roller

### `README.md`

Denna fil.

### `instruktioner/`

Innehåller instruktionen som endast gäller **laboration 3**:

```text
instruktioner/laboration3-instruktion.md
```

### `student_arbete/`

Detta är studentens arbetskatalog. Studenten ska gå till denna katalog innan programmet byggs, körs och testas.

```bash
cd laboration3/student_arbete
```

### `student_arbete/src/`

Innehåller laborationens C++-källkod:

```text
src/main.cpp
src/is_sorted.cpp
src/merge_sorted.cpp

```

### `student_arbete/include/`

Innehåller laborationens headerfiler:

```text
include/is_sorted.h
include/merge_sorted.h

```

### `student_arbete/data/`

Innehåller laborationens datafiler:

```text
data/A
data/A1
data/B
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

1. Läs `laboration3-instruktion.md`.
2. Läs relevanta dokument i `gemensamma-instruktioner/`.
3. Gå till `laboration3-sort/student_arbete/`.
4. Arbeta med ett mindre utvecklingssteg i taget.
5. Bygg och kör programmet.
6. Genomför och dokumentera relevanta tester.
7. Skapa meningsfulla commits under arbetets gång (minst 3).
8. Pusha regelbundet till ditt privata repository.
