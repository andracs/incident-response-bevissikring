# Log-øvelser: Find, læs og verificere logfiler — med AI-ekstraopgaver

**Hold:** parvis (2 studerende) · **Tid:** Ca. 3 × 45 minutter med 10 minutters pause mellem øvelserne **Udstyr:** egne Windows-, macOS- eller Linux-maskiner

**Læringsudbytte:** Efter øvelserne kan I finde og læse logfiler på Windows, macOS og Linux, og bruge AI som analyseværktøj samt verificere AI'ens output.

**OBS:** Fjernstyring i øvelse 2 sker med AnyDesk, TeamViewer eller lignende. Fjernstyringsværktøjet afinstalleres umiddelbart efter øvelse 2. AI-ekstraopgaverne udføres med anonymiserede data.

---

# Aflevering på Moodle

Samlet aflevering uploades på Moodle senest ved øvelsesperiodeens afslutning (én aflevering pr. par):

1. Notat, tidslinje og hændelsesrapport fra øvelse 1
2. Tre fund samt refleksion fra øvelse 2 (begge roller) + bekræftelse af, at fjernstyringsværktøjet er afinstalleret
3. Hash-tabel og diff-uddrag fra øvelse 3
4. Udførte ekstraopgaver: anonymiseret udsnit, feltforklaring, rival-sammenligning og stillingtagen
5. Prompt-log: anvendte prompts, AI-svar og ét konkret eksempel på, hvor AI'en tog fejl

---

## Øvelse 1 – Log-safari og makker-analyse 

**Mål:** Bliv fortrolig med hvor logfiler ligger, hvordan de er opbygget, og analysere et logudsnit, man ikke selv har produceret.

1. Find logfilerne på din maskine:
   - **Windows:** `Event Viewer` (kør: `eventvwr.msc`) — se især *Windows Logs* → *System* og *Application*.
   - **macOS:** *Console*-appen samt mappen `/var/log/` og kommandoen `log show --last 1h`.
   - **Linux:** `less /var/log/syslog` eller `journalctl --since "1 hour ago"`; gennemgå også `/var/log/` med `ls -l`.
2. Notér individuelt: Hvor ligger filerne? Hvad hedder de? Hvad er formatet (tekst, XML, tidsstempel, alvorlighedsgrad)? Er nogle komprimerede?
3. Find én konkret hændelse fra det seneste døgn, som du selv har forårsaget (login, fejlbesked, opdatering).
4. **Eksportér et udsnit** af en log (fx de seneste 50–100 linjer, eller en eksport fra Event Viewer som `.txt`/`.evtx`).
5. **Byt fil med makkeren.** Ejeren giver ingen hjælp under analysen.
6. Analysér makkerens udsnit: Lav en tidslinje med de 3–5 vigtigste linjer. Identificér fejl, advarsler og eventuelle uregelmæssigheder.
7. Skriv en kort hændelsesrapport (5–8 linjer): hvad skete der, hvornår, hvor alvorligt, og hvad vil du undersøge næste gang.
8. Gennemgå rapporten med makkeren: Var analysen korrekt, eller var der noget i loggen, som du tolkede forkert?

**Leverance:** Notat (3–5 linjer pr. person) samt tidslinje og hændelsesrapport. Diskuter til sidst: Hvilke oplysninger kunne en uvedkommende udlede af det samme udsnit?

---

## Pause 1  

---

## Øvelse 2 – Fjernstyring: Find makkerens logs med AnyDesk eller TeamViewer 

**Mål:** Naviger i logfiler på en maskine, man ikke sidder ved, via et fjernstyringsværktøj, og bruge operativsystemets egne kommandoer til at finde loggene.

> **OBS:**  Værktøjet afinstalleres umiddelbart efter øvelsen.

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

## Pause 2


---

## Øvelse 3 – Backup og verificering: Hash og diff af logfiler (45 min)

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

# Ekstraopgaver: Loganalyse med AI (til sidst)

Udføres til sidst, hvis tiden tillader — ca. 15 minutter pr. opgave. Der bruges en AI-assistent (fx Mistral Vibe eller et tilsvarende værktøj godkendt af læreren).

**Fælles regel:** Intet logudsnit indsættes i en AI, før det er anonymiseret (ekstraopgave 1). Der føres **prompt-log** for hver opgave: hvilke prompts blev brugt, hvad svarede AI'en — og ét konkret eksempel på, hvor AI'en tog fejl.

## Ekstraopgave 1 – Anonymisering før AI 

**Mål:** Fjerne persondata fra et logudsnit, før det deles med en AI — og forstå, hvilke felter der bærer hvilke oplysninger.

1. Tag udsnit fra øvelse 1 (50–100 linjer). Logfiler indeholder typisk brugernavne, IP-adresser og hostnames — intet af dette må sendes til en AI.
2. Anonymisér udsnittet med operativsystemets indbyggede kommandoer:
   - **Linux:** `sed -E 's/([0-9]{1,3}\.){3}[0-9]{1,3}/X.X.X.X/g' udsnit.txt > udsnit_anonym.txt` og `sed -i 's/<dit-brugernavn>/BRUGER/g' udsnit_anonym.txt`
   - **macOS:** samme kommandoer, men `sed -i ''` ved redigering i filen.
   - **Windows (PowerShell):** `(Get-Content udsnit.txt) -replace '(\d{1,3}\.){3}\d{1,3}','X.X.X.X' -replace '<dit-brugernavn>','BRUGER' | Set-Content udsnit_anonym.txt`
3. **Kontroller resultatet:** Søg efter dit navn, din IP og dit hostname i den anonymiserede fil (`grep -i <navn> udsnit_anonym.txt` / `Select-String -Pattern <navn> udsnit_anonym.txt`). Intet identificerende må være tilbage.

**Leverance:** Anonymiseret udsnit samt de anvendte kommandoer.

## Ekstraopgave 2 – AI som ordbog 

**Mål:** Bruge AI til at forstå logformatets opbygning — og verificere forklaringen.

1. Indsæt én anonymiseret loglinje fra ekstraopgave 1 i AI'en, og bed den forklare hvert felt "som til en ny studerende".
2. Verificér mindst ét af AI'ens forklaringer — mod selve loggen eller operativsystemets dokumentation.
3. Var der felter, AI'en ikke kunne forklare — eller forklarede forkert?

**Leverance:** Feltforklaring samt notat om, hvor og hvordan forklaringen blev verificeret.

## Ekstraopgave 3 – AI som rival, ikke assistent 

**Mål:** Sammenligne egen analyse med AI'ens — og verificere AI'ens udsagn mod råloggen.

1. Du og AI'en analyserer **hver for sig** det samme anonymiserede udsnit fra ekstraopgave 1: tidslinje og de vigtigste hændelser.
2. Sammenlign de to analyser: Hvor er I enige? Hvor uenige?
3. Indsæt begge analyser, og bed AI'en dømme: "Hvem har ret — og hvorfor?"
4. **Verificér dommen mod råloggen.** Kræv, at AI'en citerer linjenumre for sine påstande, og kontrollér hver citation. En citation, der ikke findes i loggen, er en hallucination — notér den i prompt-loggen.

**Leverance:** Sammenligning af de to analyser samt liste over verificerede og afkræftede citater.

## Ekstraopgave 4 – AI-agent og fjernadgang 

**Mål:** Reflektere over AI-agenter i systemadministration på baggrund af øvelse 2.

1. Diskuter parvis og skriv en kort stillingtagen (5–8 linjer): **Ville du give en AI-agent fjernadgang til din maskine? Hvad må den have lov til — og hvad aldrig?**
2. Understøt svaret med konkrete erfaringer fra øvelse 2: Hvilke tilladelser gav I væk med ID og adgangskode — og hvad kunne en automatiseret aktør have gjort med dem?

**Leverance:** Skriftlig stillingtagen.

