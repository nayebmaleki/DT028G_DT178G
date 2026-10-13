# Repositorystruktur för DT028G_DT178G

Detta dokument visar strukturen för kursrepositoryt `DT028G_DT178G`.

- Gemensamma instruktioner finns i katalogen `gemensamma-instruktioner/`.
- Laborationsspecifika instruktioner finns i respektive laborations katalog `instruktioner/`.
- Studentens kod och dokumentation sparas i respektive laborations katalog `student_arbete/`.

## Hela repositorystrukturen

```text
DT028G_DT178G/
│
├── README.md
├── .gitignore
│
├── gemensamma-instruktioner/
│   ├── arbetsgang_och_git_laborationer.md
│   └── testprotokoll_exempel.md
│
├── laboration1-minmaxmedel/
│   ├── README.md
│   │
│   ├── instruktioner/
│   │   └── laboration1-instruktion.md
│   │
│   └── student_arbete/
│       ├── README.md
│       ├── Makefile
│       │
│       ├── src/
│       │   └── main.cpp
│       │
│       ├── data/
│       │   └── values.txt
│       │
│       └── tester/
│           └── testprotokoll.md
│
├── laboration2-parse/
│   ├── README.md
|
│   ├── instruktioner/
│   │   └── laboration2-instruktion.md
│   │
│   └── student_arbete/
│       ├── README.md
│       ├── Makefile
│       ├── .gitignore
│       │
│       ├── src/
│       │   └── main.cpp
│       │
│       ├── data/
│       │   └── names.txt
│       │
│       └── tester/
│           └── testprotokoll.md
│
├── laboration3-sort/
│   ├── README.md
│   │
│   ├── instruktioner/
│   │   └── laboration3-instruktion.md
│   │
│   └── student_arbete/
│       ├── README.md
│       ├── Makefile
│       ├── .gitignore
│       │
│       ├── src/
│       │   └── is_sorted.cpp
│       │   └── merge_sorted.cpp
│       │   └── main.cpp
│       │
│       ├── include/
│       │   └── is_sorted.h
│       │   └── merge_sorted.h
│       │
│       ├── data/
│       │   └── A
|       |   └── B
|       |   └── A1
|       |
│       └── tester/
│           └── testprotokoll.md
│
└── laboration4-wordcount/
│   ├── README.md
│   │
│   ├── instruktioner/
│   │   └── laboration4-instruktion.md
│   │
│   └── student_arbete/
│       ├── README.md
│       ├── Makefile
│       ├── .gitignore
│       │
│       ├── src/
│       │   └── main.cpp
│       │   └── word_count.cpp
│       │
│       ├── include/
│       │   └── word_count.h
│       │
│       ├── data/
│       │   └──hitchhikersguide.txt
│       │
│       └── tester/
│            └── testprotokoll.md
│     
└── slutprojekt-bullcow/
│   ├── README.md
│   │
│   ├── instruktioner/
│   │   └── projektinstruktion-bullcow.md
│   │
│   └── student_arbete/
│       ├── README.md
│       ├── Makefile
│       ├── .gitignore
|       |
│       ├── src/
│       │   └── main.cpp
│       │
│       ├── include/
|       |
│       ├── data/
│       │   
│       └── tester/
│            └── testprotokoll.md 
|
└── slutprojekt-kontaktbok/
│   ├── README.md
│   │
│   ├── instruktioner/
│   │   └── projektinstruktion-kontaktbok.md
│   │
│   └── student_arbete/
│       ├── README.md
│       ├── Makefile
│       ├── .gitignore
|       |
│       ├── src/
│       │   └── main.cpp
│       │
│       ├── include/
|       |
│       ├── data/
│       │   
│       └── tester/
│            └── testprotokoll.md
```
