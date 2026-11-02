# Afsnit 2 · Facitliste (til studerende)

## Case 1 — Beredskabet

| Element | Vurdering | Henv. |
|---|---|---|
| CIRP indlejret i den generelle nedbrudsplan | **Forkert** – en CIRP bør udarbejdes for sig, den bliver typisk omfattende med step-by-step-guider | 2.01 |
| Definition af større hændelse, kontaktoplysninger, hvornår politiet involveres | **Korrekt** – det er blandt guidens anbefalede CIRP-indhold | 2.01 |
| Årlig øvedag med simuleret angreb | **Korrekt** – øvelser sikrer, at planen huskes, og at kun relevante personer går i gang | 2.01 |
| Netværksdiagram fra 2015, aldrig opdateret | **Forkert** – diagrammet skal vedligeholdes, når systemer tilføjes/fjernes | 2.02 |
| Straks genoprettelse fra backup uden bevissikring | **Forkert** – sikres beviserne grundlæggende ikke, inden systemerne gendannes, vanskeliggøres en evt. retssag | 1.04, 3.02 |
| Backup som netværksdrev på filserveren | **Forkert** – backup-systemet skal isoleres fra netværket; ellers krypterer ransomware den også | 2.07 |

## Case 2 — Logning og tid

| Element | Vurdering | Henv. |
|---|---|---|
| GDPR forbyder anden logning | **Forkert** – guiden påpeger, at logning tværtimod kan være *lovpligtig*, bl.a. efter GDPR | 2.06 |
| Kun firewall logges | **Forkert** – guiden lister en række kritiske kilder (router, IDS/IPS, DHCP, AD, adgangslogs m.fl.), som politiet ofte mangler | 2.06 |
| DHCP-logs gemmes kun 72 timer | **Forkert** – netop DHCP-logs glemmes eller overskrives, før politiet involveres; og DHCP-tilknytningen er ofte det, der knytter en IP til en maskine | 1.03, 2.06 |
| Alle enheder synkroniseret via NTP | **Korrekt i sig selv** – fælles tid er afgørende; bare 1/100 sekund har betydning | 2.05 |
| Ny enhed uden tidssynkronisering | **Forkert** – der skal være procedurer, så nye enheder synkroniseres og eksisterende tjekkes | 2.05 |
| Ugentligt tjek af SIEM | **Forkert** – "det er ikke nok med et ugentligt tjek"; systemerne bør monitoreres konstant, og hackerne arbejder sjældent 9–17 | 2.06 |

## Case 3 — Rettigheder og segmentering

| Element | Vurdering | Henv. |
|---|---|---|
| Ransomware har kun adgang til det, den inficerede bruger har adgang til | **Korrekt** – det er bogholderens adgangsprofil, der bestemmer skadesomfanget | 2.04 |
| Alle har administratorrettigheder | **Forkert** – brugere bør kun have de rettigheder, de har brug for; alt for ofte har medarbejdere admin-rettigheder uden behov | 2.03 |
| Direktøren skal have adgang til alt | **Forkert** – "selv den administrerende direktør behøver ikke at kunne tilgå alt" | 2.03 |
| Ingen segmentering, for truslen kommer udefra | **Forkert** – dobbelt fejl: dels skal netværket segmenteres, dels er en meget stor del af NC3's sager *insider*-sager; gå ud fra, at netværket allerede er kompromitteret (assume breach) | 1.04, 2.04 |
| To-faktor på kritiske systemer | **Korrekt anbefaling** – to-faktor på følsomme områder (fx backup og logserver) anbefales | 2.03, 2.04 |

## Case 4 — Insidere og anmeldelse

| Element | Vurdering | Henv. |
|---|---|---|
| Insider-mistanke afvises | **Forkert** – en meget stor del af de hændelser, NC3 inddrages i, omhandler insidere; gamle, inaktive brugere er ideelle for hackere at overtage | 1.04, 2.03 |
| Opsagt medarbejder har stadig aktiv admin-profil | **Realistisk fælde** – gamle brugere bør slettes ved fratrædelse | 2.03 |
| Opkald til NC3 = anmeldelse | **Forkert** – "et opkald til NC3 er ikke en anmeldelse"; anmeldelse sker kun via det lokale politi (eller online på politi.dk) | 3.04 |
| Det lokale politi behøver ikke involveres | **Forkert** – som udgangspunkt indgives anmeldelsen til det lokale politi, der kan trække på NC3 | 3.04 |
| Detaljeret log over handlinger med tid, hvem og hvordan | **Korrekt** – kontaktpersonen bør føre præcis log med nøjagtige tidspunkter | 3.02, 3.05 |

## Case 5 — Bevissikring

| Element | Vurdering | Henv. |
|---|---|---|
| Log over handlinger under sikringen | **Korrekt** – tidspunkt, hvem og hvordan skal nedskrives for hver handling | 3.05 |
| Harddisk sikres først, RAM bagefter | **Forkert** – rækkefølgen er: 1) volatile data (RAM), 2) offline data (harddisk), 3) yderligere oplysninger; RAM forsvinder, når maskinen lukkes | 3.05 |
| Dekryptering før sikring | **Forkert** – en krypteret enhed skal *ikke* dekrypteres inden sikring; dekryptering kan potentielt ødelægge beviser | 3.05 |
| Navngivning "Lars-PC-kopi-FINAL" | **Forkert** – der bør være en fælles standard: 'Enhed 1', 'Enhed 2' osv. med et sideløbende dokument; personnavne giver forvirring | 3.05 |
| Kopier i privat OneDrive | **Forkert** (samme princip) – beviser skal sikres med dataintegritet og hash umiddelbart efter sikring, så man ikke arbejder på ændret data; adgangskontrol til materialet er del af integritetskravet | 1.05, 3.05 |
| Hashværdi af sikret data | **Korrekt fremgangsmåde**, hvis den nævnes – ellers et oplagt punkt for forbedringsforslag | 3.05 |

## Case 6 — Kommunikation under angreb

| Element | Vurdering | Henv. |
|---|---|---|
| Detaljeret log med tidspunkter påbegyndes straks | **Korrekt** – kontaktpersonen bør så hurtigt som muligt føre en log over, hvad der foretages, inkl. tidspunkt | 3.02 |
| Studentermedhjælper som kontaktperson | **Forkert** – der skal udpeges en *kompetent* person med træning/erfaring i it-sikkerhedskriser – og gerne en alternativ | 3.01 |
| E-mail-varsling til alle, inkl. hackeren | **Forkert** – ved en decideret indtrængning bør e-mail undgås, da hackerne kan overvåge den og opdage, at de er afsløret | 3.02 |
| Aktuelt kompromitteret system giver færrest beviser | **Forkert** – det er *omvendt*: ved et aktuelt kompromitteret system er der størst mulighed for at sikre beviser, for hackere skjuler deres færden, inden de forlader systemet | 3.03 |
| Vent med politiet til der er fuldt overblik | **Forkert** – ved aktuelt kompromitteret system bør politiet inddrages *med det samme*, gerne via uformel henvendelse; men: anmeldelse går fortsat via det lokale politi | 3.03, 3.04 |

## Case 7 — Overvågning og awareness

| Element | Vurdering | Henv. |
|---|---|---|
| Ugentligt fredagstjek af SIEM | **Forkert** – "det er ikke nok med et ugentligt tjek"; konstant monitorering, og vagtordningen skal tage højde for, at hackerne sjældent arbejder inden for normal kontortid | 2.06 |
| Alle regler slået fra pga. falske positiver | **Forkert** – reglerne skal finjusteres; slås de fra, drukner hændelsen eller opdages slet ikke | 2.06 |
| Træning er overflødigt, netværket er sikret udefra | **Forkert (dobbelte fejl)** – et netværk kan være lukket udefra og stadig usikkert over for medarbejderes adfærd (spearphishing, social engineering); og det er netop den utilsigtede aktør, der ofte åbner døren | 1.04, 2.10 |
| Awareness kun for it-folk, direktøren undtaget | **Forkert** – uddannelse skal omfatte alle med adgang til systemerne, "fra direktøren til studentermedhjælperen" | 2.10 |
| Falske phishing-kampagner mod egne medarbejdere | **Korrekt** – guiden anbefaler netop løbende kampagner med falske svindelforsøg | 2.10 |
| Kontrolopkald ved store overførsler | **Korrekt** – retningslinje mod BEC/CEO-fraud: overførsel over et vist beløb via både e-mail og kontrolopkald | 2.10 |
