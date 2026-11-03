# Log-øvelser: Fire parvise øvelser i at finde, læse og verificere logfiler

**Hold:** parvis (2 studerende) · **Tid:** 4 × 30 minutter med 10 minutters pause mellem øvelserne (samlet ca. 2 timer 40 min) · **Udstyr:** egne Windows-, macOS- eller Linux-maskiner

**Læringsudbytte:** Efter øvelserne kan den studerende lokalisere og genkende logformater på Windows, macOS og Linux; analysere og formidle hændelser ud fra logdata; fjernstyre en maskine og finde logfiler eksternt; samt tage backup af logfiler og verificere ændringer med hash-værdier og diff.

**Rammer:** Øvelserne udføres kun på skolens netværk og kun med makkerens udtrykkelige tilladelse. Fjernstyring i øvelse 3 sker med AnyDesk, TeamViewer eller lignende. Alle kommandoeksempler i øvelserne bruger operativsystemets indbyggede (native) kommandoer og værktøjer. Fjernstyringsværktøjet afinstalleres umiddelbart efter øvelse 3.

---

## Øvelse 1 – Log-safari: Find dine egne logfiler (30 min)

**Mål:** Blive fortrolig med hvor logfiler ligger, og hvordan de er opbygget, på eget operativsystem.

1. Find logfilerne på din maskine:
   - **Windows:** `Event Viewer` (kør: `eventvwr.msc`) — se især *Windows Logs* → *System* og *Application*.
   - **macOS:** *Console*-appen samt mappen `/var/log/` og kommandoen `log show --last 1h`.
   - **Linux:** `less /var/log/syslog` eller `journalctl --since "1 hour ago"`; gennemgå også `/var/log/` med `ls -l`.
2. Notér individuelt: Hvor ligger filerne? Hvad hedder de? Hvad er formatet (tekst, XML, tidsstempel, alvorlighedsgrad)?
3. Find én konkret hændelse fra det seneste døgn, som du selv har forårsaget (login, fejlbesked, opdatering).
4. Byt skærm med makkeren: Forklar — uden at røre tastaturet — hvor din hændelse ligger, og hvad den betyder.

**Leverance:** Notat på 3–5 linjer pr. person: sti til loggen samt hændelsen fortolket med egne ord.

---

## Pause 1 (10 min) — Opsamling i plenum

Hvad er den største forskel på logformaterne på Windows, macOS og Linux? Hvilket OS logfæster mest — og hvad betyder det for efterforskning?

---

## Øvelse 2 – Makker-analysen: Læs en fremmed log (30 min)

**Mål:** Analysere et logudsnit, man ikke selv har produceret.

1. Eksportér et udsnit af en log fra øvelse 1 (fx de seneste 50–100 linjer, eller en eksport fra Event Viewer som `.txt`/`.evtx`).
2. Byt fil med makkeren. Ejeren giver ingen hjælp under analysen.
3. Analysér makkerens udsnit: Lav en tidslinje med de 3–5 vigtigste linjer. Identificér fejl, advarsler og eventuelle uregelmæssigheder.
4. Skriv en kort hændelsesrapport (5–8 linjer): hvad skete der, hvornår, hvor alvorligt, og hvad vil du undersøge næste gang.
5. Gennemgå rapporten med makkeren: Var analysen korrekt, eller var der noget i loggen, som du tolkede forkert?

**Leverance:** Tidslinje og hændelsesrapport. Diskuterer til sidst: Hvilke oplysninger kunne en uvedkommende udlede af det samme udsnit?

---

## Pause 2 (10 min) — Opsamling i plenum

Kort fælles opsamling: Hvorfor tolkede nogen par loggen forkert? Hvilke fejltyper var sværest at identificere? Afrunding af makkerens rolle: hvordan stillede man de rigtige spørgsmål uden at afsløre svaret?

---

## Øvelse 3 – Fjernstyring: Find makkerens logs med AnyDesk eller TeamViewer (30 min)

**Mål:** Navigere i logfiler på en maskine, man ikke sidder ved, via et fjernstyringsværktøj — og bruge operativsystemets egne kommandoer til at finde loggene.

> **OBS:** Kun på skolens netværk og kun med makkerens samtykke. Værktøjet afinstalleres umiddelbart efter øvelsen.

1. Installer **AnyDesk** eller **TeamViewer** (eller et lignende værktøj godkendt af læreren) på begge maskiner.
2. Makkeren deler sit ID og adgangskode; du opretter forbindelse og overtager styringen af skrivebordet.
3. Find via fjernstyring **tre logkilder**: én systemlog, én applikationslog og én sikkerhedsrelateret hændelse (login, sudo eller mislykket loginforsøg). Brug operativsystemets indbyggede kommandoer på fjernmaskinen:
   - **Windows:** `Get-WinEvent -LogName System -MaxEvents 20` (PowerShell) eller `wevtutil qe System /c:20`
   - **macOS:** `log show --last 1h` og `/var/log/`
   - **Linux:** `journalctl --since "1 hour ago"` og `less /var/log/auth.log`
4. Notér de tre fund med tidsstempel (eller tag skærmbillede).
5. **Byt roller:** Makkeren overtager din maskine og gentager øvelsen.
6. **Afinstaller fjernstyringsværktøjet på begge maskiner** og bekræft over for hinanden, at det er sket.

**Leverance:** Tre fund pr. person samt kort refleksion: Hvad kræver fjernadgang af teknik og tillid? Hvad adskiller fjernsupport fra uautoriseret adgang?

---

## Pause 3 (10 min) — Opsamling i plenum

Hvad er forskellen på at sidde ved og at fjernstyre en maskine? Hvilke tilladelser giver man væk, når man deler sit ID og sin adgangskode — og hvorfor er det vigtigt, at værktøjet afinstalleres efter brug? Brug pausen til at sikre, at afinstallationen er gennemført på begge maskiner.

---

## Øvelse 4 – Backup og verificering: Hash og diff af logfiler (30 min)

**Mål:** Tage backup af logfiler og verificere med hash og diff, at filer er ændret — og hvad ændringen indeholder.

1. **Tag backup 1** af en logmappe:
   - **Windows:** kopiér logudsnit til en mappe `backup1`, fx `robocopy <logsti> backup1 /E`
   - **macOS/Linux:** `mkdir -p backup1 && cp /var/log/*.log backup1/`
2. **Beregn hash-værdier** for filerne i `backup1`:
   - **Windows:** `certutil -hashfile backup1\<fil> SHA256`
   - **macOS:** `shasum -a 256 backup1/<fil>`
   - **Linux:** `sha256sum backup1/<fil>`
   Notér hash-værdierne.
3. **Skab aktivitet:** Log af og på, start og luk et program, afbryd netværket kort, indsæt en USB-nøgle — gerne noget, din makker ikke kender til.
4. **Tag backup 2** til en separat mappe (`backup2`).
5. **Beregn hash igen** på de samme filer i `backup2` og sammenlign:
   - Er hash-værdien ens, er filen uændret. Er den forskellig, er filen ændret — og så er diff næste skridt.
6. **Diff de to backups** og identificér, hvad makkeren faktisk gjorde:
   - **macOS/Linux:** `diff -r backup1 backup2`
   - **Windows (PowerShell):** `Compare-Object (Get-Content backup1\<fil>) (Get-Content backup2\<fil>)`
7. Gæt først ud fra hash og diff, og bekræft derefter med makkeren. Var alle aktiviteter synlige i loggen?

**Leverance:** Tabel med fil, hash før/hash efter og ændret/uændret, samt diff-uddrag. Reflekter kort: Hvorfor er hash en pålidelig metode til at dokumentere, at en fil er ændret? Hvad sker der, hvis en angriber ændrer loggen mellem to backups?

---

## Aflevering på Moodle

Samlet aflevering uploades på Moodle senest ved øvelsesperiodeens afslutning (én aflevering pr. par):

1. Notat fra øvelse 1 (begge persons noter)
2. Tidslinje og hændelsesrapport fra øvelse 2
3. Tre fund samt refleksion fra øvelse 3 (begge roller) + bekræftelse af, at fjernstyringsværktøjet er afinstalleret
4. Hash-tabel og diff-uddrag fra øvelse 4
