# Stikordsliste · Incident response

Grupperet og forenklet – til repetition og eksamen. Afsnitsnumrene henviser til NC3-guiden.

## Logning

- Logning kan være **lovpligtig** – bl.a. efter GDPR (2.06)
- **Kritiske kilder**, politiet ofte mangler: router, IDS/IPS, DHCP, AD, adgangslogs, proxy, DMZ, gæstenetværk, antivirus, event logs (2.06)
- **DHCP-log** = det, der knytter en IP-adresse til en maskine (1.03, 2.06)
- Logs bliver **overskrivne** – tag aktivt stilling til hvad og hvor længe (2.06)
- SIEM samler logs + alarmer – regler skal **finjusteres** (2.06)
- **NTP**: fælles tid på hele netværket – 1/100 sekund betyder noget; procedure for nye enheder (2.05)

## Monitorering

- **Konstant** overvågning – et ugentligt tjek er ikke nok (2.06)
- Hackerne arbejder **sjældent 9–17** → vagtordning uden for kontortid
- Uden finjustering: **falske positiver** → hændelsen drukner eller ignoreres

## Insidere

- Meget stor del af NC3's sager = **insidere** (1.04)
- **Assume breach** – gå ud fra, at netværket allerede er kompromitteret (1.04, 2.04)
- **Gamle/inaktive brugerprofiler** er ideelle at overtage → slet ved fratrædelse (2.03)

## Bevissikring

- Rækkefølge: **1) volatile data (RAM) → 2) offline data (harddisk) → 3) yderligere oplysninger** (3.05)
- **RAM forsvinder** ved nedlukning (3.05)
- Krypteret enhed: **IKKE dekryptér** før sikring – dekryptering kan ødelægge beviser (3.05)
- Log alle handlinger: **tid · hvem · hvordan** (3.05)
- Navnestandard: **"Enhed 1", "Enhed 2"** + sideløbende dokument (3.05)
- **Hash** af alt sikret data umiddelbart efter sikring (3.05)
- Undgå **e-mail** ved aktiv indtrængning – hackeren kan overvåge (3.02)

## Anmeldelse (2026)

- **Politianmeldelse:** digitalt via [politi.dk → Anmeld kriminalitet → Digital kriminalitet](https://politi.dk/anmeld-kriminalitet/digital-kriminalitet) – dækker hacking, ransomware, DDoS
- Kræver **MitID** (virksomheder: MitID Erhverv); alternativt **114** eller personligt på politistation
- Kvittering + **journalnummer i Digital Post**
- **Tip ≠ anmeldelse**
- **GDPR:** brud på persondatasikkerheden → anmeld til **Datatilsynet via Virk.dk**, uden unødig forsinkelse og senest **72 timer** (art. 33); høj risiko → **underret de registrerede** (art. 34) – se [Datatilsynet: Anmeld sikkerhedsbrud](https://www.datatilsynet.dk/sikkerhedsbrud/anmeld-sikkerhedsbrud)
- **NIS2** (væsentlige/essentielle enheder): tidlig varsling **24 timer**, underretning **72 timer**, slutrapport

## Datatilsynets 10 typiske brud

- **Tre brudtyper:** fortrolighed · integritet · tilgængelighed
- Typikere: fejlsendte data (auto-complete, forkert modtager), eksponeret beskyttet adresse, fejludlevering, manglende sletning, tab/tyveri af **ukrypteret** enhed, **for bred adgang** på netværksdrev, kodefejl/dårligt design, data gemt i skabeloner, **ransomware**
- **Passende foranstaltninger** (GDPR art. 32) – risikovurdering for de **berørte personer**, ikke for forretningen
- **Menneskelige fejl** = hyppigste årsag → retningslinjer, uddannelse, awareness-kampagner
- Sikkerhed er både **teknisk og organisatorisk** – "privacy by design"
- Kilde: [Datatilsynet: De 10 brud](https://www.datatilsynet.dk/regler-og-vejledning/behandlingssikkerhed/de-10-brud)
