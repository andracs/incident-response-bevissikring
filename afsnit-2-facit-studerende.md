# Afsnit 2 · Facitliste (til studerende)

## Scenarie 1 — Beredskabet

| Element | Vurdering |
|---|---|
| CIRP indlejret i den generelle nedbrudsplan | **Forkert** – en CIRP bør udarbejdes for sig, den bliver typisk omfattende med step-by-step-guider |
| Definition af større hændelse, kontaktoplysninger, hvornår politiet involveres | **Korrekt** – det er blandt guidens anbefalede CIRP-indhold |
| Årlig øvedag med simuleret angreb | **Korrekt** – øvelser sikrer, at planen huskes, og at kun relevante personer går i gang |
| Netværksdiagram fra 2022, aldrig opdateret | **Forkert** – diagrammet skal vedligeholdes, når systemer tilføjes/fjernes |
| Straks genoprettelse fra backup uden bevissikring | **Forkert** – sikres beviserne grundlæggende ikke, inden systemerne gendannes, vanskeliggøres en evt. retssag |
| Backup som netværksdrev på filserveren | **Forkert** – backup-systemet skal isoleres fra netværket; ellers krypterer ransomware den også |

## Scenarie 2 — Logning og tid

| Element | Vurdering |
|---|---|
| GDPR forbyder anden logning | **Forkert** – guiden påpeger, at logning tværtimod kan være *lovpligtig*, bl.a. efter GDPR |
| Kun firewall logges | **Forkert** – guiden lister en række kritiske kilder (router, IDS/IPS, DHCP, AD, adgangslogs m.fl.), som politiet ofte mangler |
| DHCP-logs gemmes kun 72 timer | **Forkert** – netop DHCP-logs glemmes eller overskrives, før politiet involveres; og DHCP-tilknytningen er ofte det, der knytter en IP til en maskine |
| Alle enheder synkroniseret via NTP | **Korrekt i sig selv** – fælles tid er afgørende; bare 1/100 sekund har betydning |
| Ny enhed uden tidssynkronisering | **Forkert** – der skal være procedurer, så nye enheder synkroniseres og eksisterende tjekkes |
| Ugentligt tjek af SIEM | **Forkert** – "det er ikke nok med et ugentligt tjek"; systemerne bør monitoreres konstant, og hackerne arbejder sjældent 9–17 |

## Scenarie 3 — Bevissikring

| Element | Vurdering |
|---|---|
| Log over handlinger under sikringen | **Korrekt** – tidspunkt, hvem og hvordan skal nedskrives for hver handling |
| Harddisk sikres først, RAM bagefter | **Forkert** – rækkefølgen er: 1) volatile data (RAM), 2) offline data (harddisk), 3) yderligere oplysninger; RAM forsvinder, når maskinen lukkes |
| Dekryptering før sikring | **Forkert** – en krypteret enhed skal *ikke* dekrypteres inden sikring; dekryptering kan potentielt ødelægge beviser |
| Navngivning "Lars-PC-kopi-FINAL" | **Forkert** – der bør være en fælles standard: 'Enhed 1', 'Enhed 2' osv. med et sideløbende dokument; personnavne giver forvirring |
| Kopier i privat OneDrive | **Forkert** (samme princip) – beviser skal sikres med dataintegritet og hash umiddelbart efter sikring, så man ikke arbejder på ændret data; adgangskontrol til materialet er del af integritetskravet |
| Hashværdi af sikret data | **Korrekt fremgangsmåde**, hvis den nævnes – ellers et oplagt punkt for forbedringsforslag |

## Scenarie 4 — Kommunikation under angreb

| Element | Vurdering |
|---|---|
| Detaljeret log med tidspunkter påbegyndes straks | **Korrekt** – kontaktpersonen bør så hurtigt som muligt føre en log over, hvad der foretages, inkl. tidspunkt |
| Studentermedhjælper som kontaktperson | **Forkert** – der skal udpeges en *kompetent* person med træning/erfaring i it-sikkerhedskriser – og gerne en alternativ |
| E-mail-varsling til alle, inkl. hackeren | **Forkert** – ved en decideret indtrængning bør e-mail undgås, da hackerne kan overvåge den og opdage, at de er afsløret |
| Aktuelt kompromitteret system giver færrest beviser | **Forkert** – det er *omvendt*: ved et aktuelt kompromitteret system er der størst mulighed for at sikre beviser, for hackere skjuler deres færden, inden de forlader systemet |
| Vent med politiet til der er fuldt overblik | **Forkert** – ved aktuelt kompromitteret system bør politiet inddrages *med det samme*, gerne via uformel henvendelse. Selve anmeldelsen sker i dag digitalt via politi.dk – se note nedenfor |

## Scenarie 5 — Business continuity

| Element | Vurdering |
|---|---|
| Defineret genoprettelsesfrist (24 timer) for kritiske systemer | **Korrekt** – krav til genoprettelsestid bør aftales og skrives ned på forhånd, så prioriteringen er klar, når hændelsen er løs |
| Backup isoleret fra det øvrige netværk | **Korrekt** – backup-systemet skal isoleres fra netværket, så ransomware ikke når den også |
| Straks gendannelse uden at sikre logs og RAM | **Forkert** – beviser skal sikres, *inden* systemerne gendannes; procedurerne skal sikre, at det kan ske hurtigt, ikke udelades |
| Gendannelse fra nyeste backup uden kortlægning af gerningstidsrummet | **Forkert** – der kan være forberedende handlinger lang tid forud for hændelsen; vælges et gendannelsespunkt efter kompromitteringen, genindsættes angriberens fodfæste, og arbejdet starter forfra |
| Pressemeddelelse som kundekommunikation | **Delvist korrekt** – en CIRP bør definere, hvem der må udtale sig til pressen og hvornår; kommunikationen skal være målrettet og rettidig – ikke automatisk ud til alle |
| Medarbejdere underrettes via fælles e-mail | **Delvist forkert** – e-mail kan være nede eller kompromitteret; ved en indtrængning kan hackerne overvåge e-mailen, så alternative kanaler bør være planlagt |
| Ingen evaluering eller opdatering af planen | **Forkert** – en CIRP skal vedligeholdes og trænes løbende; efter en hændelse skal der evaluering til, så næste søndag nat går bedre |

---

## Note · Anmeldelse i 2026

Guidens procedure ("anmeldelse indgives til det lokale politi") er delvist forældet. I dag gælder:

- **Politianmeldelse:** Hacking, ransomware og DDoS anmeldes digitalt via [politi.dk → Anmeld kriminalitet → Digital kriminalitet](https://politi.dk/anmeld-kriminalitet/digital-kriminalitet). Kræver MitID – for virksomheder typisk MitID Erhverv. Alternativt: ring 114 eller mød personligt op på en politistation. Politiet sender kvittering med journalnummer i Digital Post.
- **Tip ≠ anmeldelse** – et tip til politiet er ikke en anmeldelse.
- **Datatilsynet:** Ved brud på persondatasikkerheden skal den dataansvarlige *desuden* anmelde bruddet til Datatilsynet via Virk.dk – uden unødig forsinkelse og om muligt senest 72 timer efter opdagelsen (GDPR art. 33). Ved høj risiko for de registrerede skal de også underrettes direkte (art. 34). Se [Datatilsynet: Anmeld sikkerhedsbrud](https://www.datatilsynet.dk/sikkerhedsbrud/anmeld-sikkerhedsbrud).
- **NIS2:** Væsentlige og essentielle enheder (fx kritisk infrastruktur og digitale tjenester) har egne indberetningsfrister til cybermyndighederne: tidlig varsling inden for 24 timer og underretning inden 72 timer.
