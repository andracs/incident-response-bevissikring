# Beredskab og business continouity opgaver

## Analysér forskellige incident response eksempler

I kan herunder finde nogle udsagn fra en virksomheds it-sikkerhedspraksis. For hvert udsagn skal du:

1. **Identificér** de enkelte påstande i udsagnet (der er typisk 4–7 pr. udsagn).
2. **Vurdér** hver påstand: korrekt, forkert eller delvist korrekt.
3. **Korrigér** de forkerte elementer: hvad skulle virksomheden have gjort i stedet?
4. **Prioritér**: peg på den fejl i udsagnet, der efter din mening er den *dyreste* i en reelt hændelse, og begrund, hvorfor den slår de andre.
5. **Sammenfativ** til sidst: Hvilket gennemgående mønster ser du på tværs af udsagnene?

**Kilde:** Rigspolitiets NC3 & Dansk IT: *Virksomhedsguide – Forholdsregler ved brud på it-sikkerhedssystemer* (se på Moodle).

---

### Case 1 — Beredskabet: "Vi har jo en plan"

> "Virksomheden har udarbejdet en omfattende beredskabsplan, hvor CIRP-indholdet (Computer Incident Response Plan) er indlejret som afsnit 4 i den generelle nedbrudsplan, så alt samles ét sted. Planen indeholder en definition af, hvad der er en større it-relateret hændelse, kontaktoplysninger på de ansvarlige samt oplysninger om, hvornår politiet skal ringes til – og hvert år holder it-afdelingen en øvedag med simuleret angreb. Netværksdiagrammet fra 2022 hænger på it-chefens kontor. Da en ransomware-episode rammer en tirsdag nat, genopretter den vagthavende teknikker straks systemerne fra backuppen, der ligger som netværksdrev på filserveren, så driften er oppe inden direktørens kaffe."

### Case 2 — Logning og tid: "Vi logger det, vi må"

> "Af hensyn til GDPR logger virksomheden kun firewall-logs, for persondataforordningen forbyder i øvrigt at gemme andre logs. DHCP-loggerne gemmes kun 72 timer, men det er der ingen, der har savnet. Til gengæld er alle servere og arbejdsstationer synkroniseret via virksomhedens NTP-server, den nye databaseserver fra i forrige måned kører dog stadig på fabriksindstillet tid. Sikkerhedsansvarlig tjekker SIEM-værktøjet hver fredag formiddag, hvor alarmerne fra ugen gennemgås."

### Case 3 — Rettigheder og segmentering: "Vi stoler på vores folk"

> "Da en bogholder åbner en inficeret vedhæftning, får ransomwaren straks frit spil: Alle medarbejdere har administratorrettigheder for at undgå support-flaskehalse, og direktøren har naturligvis adgang til alt. Direktører er jo betroede personer. Netværket er ikke segmenteret, hvilket ikke er et problem, for truslen kommer udefra, og ransomware kan i princippet kun kryptere de områder, som den inficerede bruger har adgang til. Virksomheden overvejer to-faktor-godkendelse på økonomisystemet, men har parkeret det til næste års it-budget."

### Case 4 — Insidere og anmeldelse: "Sagen er klar, vi ringer til NC3"

> "Da it-afdelingen opdager mistænkelig adgang til filserveren natten mellem fredag og lørdag, konkluderer sikkerhedschefen straks, at det må være en hacker udefra. Insider-mistanke kan afvises, selvom en medarbejder, der for tre uger siden fik opsigelse, stadig har en aktiv brugerprofil med administratorrettigheder. Chefen ringer om morgenen til NC3 og regner sagen for anmeldt; det lokale politi behøver ikke involveres, da NC3 jo er politiet. Han noterer omhyggeligt tidspunktet for opkaldet, hvem der foretog det, og hvordan hændelsen blev opdaget."

### Case 5 — Bevissikring: "Vi rydder op, mens det er varmt"

> "Manden fra it-supporten når frem kl. 08.15 og går systematisk til værks: Først tager han et fuldt spejl af harddiskene på de berørte maskiner, derefter sikrer han RAM'en på den ene laptop, der stadig kører. Den krypterede laptop dekrypterer han først med it-chefens kodeord, så materialet er lettere at læse for politiet. Undervejs nedskriver han, hvad han foretager sig, og til sidst navngiver han de sikrede kopier 'Lars-PC-kopi-FINAL' og 'Per-bærbar-2' og lægger dem i sin personlige OneDrive-mappe, så de er let tilgængelige."

### Case 6 — Kommunikation under angreb

> "Kl. 14.07 konstaterer netværksafdelingen, at en udefrakommende aktør sandsynligvis *stadig* er koblet på systemet. Udpegningen af kontaktperson lander hurtigt: den studentermedhjælper (ikke Karl), der tilfældigvis sidder tættest på telefonen, får opgaven, han kender jo alle systemerne. For at varsle medarbejderne sender it-chefen en e-mail til hele virksomheden med overskriften 'VI ER HACKEDE – LUK ALT'. Da et aktuelt kompromitteret system typisk giver de *færreste* beviser, beslutter man at vente med at kontakte politiet, til man har fuldt overblik over angriberens hensigter. Til gengæld begynder kontaktpersonen straks at føre en detaljeret log med nøjagtige tidspunkter."

### Case 7 — Overvågning og awareness: "Fredag er sikkerhedsdag"

> "Virksomheden har købt et dyrt SIEM-værktøj, som den sikkerhedsansvarlige gennemgår hver fredag mellem to møder. Da reglerne genererede alt for mange falske positiver, blev de alle slået fra, nu er panelet roligt og overdådigt grønt. Træning er overflødigt: netværket er fuldt sikret mod indtrængning udefra, og de ansatte, der alligevel vil klikke på et ondsindet link, kan intet stille op. Awareness-kurser er kun for it-afdelingen; direktøren er overhovedet ikke omfattet, da lederes kalendere ikke tillader det. Til gengæld planlægger HR at hyre et firma til at lave falske phishing-kampagner mod medarbejderne, og retningslinjen om, at pengeoverførsler over et vist beløb altid skal bekræftes med et kontrolopkald, er netop trådt i kraft."
