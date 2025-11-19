# Filter CSV by Age

Et C-program der læser en CSV-fil linje for linje, splitter hver række i navn og alder, filtrerer baseret på en angivet maksimal alder og skriver de gyldige rækker til output.  
Programmet håndterer fejl i input (blanke linjer, manglende alder, ikke-numerisk alder), men fortsætter altid behandlingen.

---

## Use
```bash
gcc -std=c11 -Wall -Wextra -O0 -g FilterCSV.c -o FilterCSV
./FilterCSV max-age [input-file] [output-file]
```

Examples:

```bash
./FilterCSV 17 people.csv out.csv
./FilterCSV 12 people.csv
cat people.csv | ./FilterCSV 20
```

The program:

- Læser input linje-for-linje med `fgets()`.
- Ignorerer blanke linjer og skriver fejl til stderr.
- Splitter hver linje i `name` og `age_str` vha. `strtok()`.
- Konverterer alder til heltal med `sscanf()`.
- Skriver kun linjer hvor `age <= max_age`.
- Håndterer alle fejltyper uden at stoppe programmet.

Files:

- **FilterCSV.c** – Hele programmet (argumenthåndtering, filåbning, parsing og filtrering).
- **input.csv** *(valgfrit)* – Eksempel på CSV med navn og alder.
- **output.csv** *(valgfrit)* – Filen programmet skriver de filtrerede rækker til.

Functions:

- `filter_stream()` – Håndterer al linje-for-linje behandling og filtrering.
- `main()` – Parser argumenter, åbner filer og kalder `filter_stream()`.
- `strtok()` (fra stdlib) – Bruges til at splitte “name,age”.
- `sscanf()` – Bruges til at konvertere alder til et heltal.
