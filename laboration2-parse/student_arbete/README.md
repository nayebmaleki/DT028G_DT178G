# Studentens arbetsyta

Allt arbete som hör till din lösning ska ligga här.

```text
student_arbete/
├── Makefile
├── README.md
├── src/
│   └── main.cpp
├── data/
│   └── names.txt
└── tester/
    └── testprotokoll.md
```

## Bygg och kör

```bash
make
./parse
```

Programmet ska använda fil-I/O och själv öppna `data/names.txt` samt skapa `data/output.txt`.

Börja med små egna testfiler. Byt till den stora `names.txt` först när kärnlogiken fungerar.
