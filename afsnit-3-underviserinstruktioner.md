# Afsnit 3 · Underviserinstruktioner

## Designrationale

Hvert udsagn er en lille case, der *blander* korrekte og forkerte elementer fra NC3-guiden. Eleven skal skille rigtigt fra forkert, begrundet med materialet – ikke bare afkrydse sandt/falsk. Fælderne er bevidst valgt blandt de fejl, NC3 selv møder i praksis: overskrevne logs, forkert bevissikring, backup på netværket og "vi ringer da bare til NC3, så er sagen anmeldt".

Cases dækker guidens rygrad: beredskab (CIRP), logning/tid, bevissikring og kommunikation under angreb.

**Den gennemgående pointe** (ventet svarretning på elevspørgsmål 5 om mønster): beviser har kort halveringstid – logs overskrives, RAM forsvinder, backup overskrives – og guidens kerneregel er, at sikring af spor skal tænkes *før* hændelsen, ikke under den.

## Brug af materialet

- **Afsnit 1** uddeles som selve opgaven (evt. én case pr. gruppe).
- **Afsnit 2** uddeles som facit, når grupperne har fremlagt – eller bruges som peer-feedback: grupperne retter hinandens analyser efter facitlisten.
- **Sværhedsgrader:**
  - **Let:** Fjern facit-tabellerne og giv udsagnene som rene sandhed/falsk-analyser uden tekstmaterialet.
  - **Sværere:** Fjern et par af de *korrekte* elementer, så eleverne selv skal tilføje, hvad virksomheden gjorde rigtigt – omvendt konstruktionslogik.
  - **Eksamen:** Lad eleverne selv skrive case nr. 5 i samme stil (fx om patch-niveau, gæstenetværk eller netværksdiagrammet som arbejdsdokument vs. sagsmateriale) og byt med en medstuderende.

## Anmeldelse i 2026 (opdateret procedure)

Guidens afsnit 3.04 (anmeldelse via det lokale politi) afspejler praksis, da guiden udkom. Den aktuelle procedure:

- **Politianmeldelse:** Digitalt via [politi.dk → Anmeld kriminalitet → Digital kriminalitet](https://politi.dk/anmeld-kriminalitet/digital-kriminalitet) – dækker hacking, ransomware og DDoS-angreb. Kræver MitID; virksomheder bruger typisk MitID Erhverv. Alternativt 114 eller personligt fremmøde på politistation. Kvittering og journalnummer sendes i Digital Post.
- **Datatilsynet:** Brud på persondatasikkerheden anmeldes af den dataansvarlige via Virk.dk, uden unødig forsinkelse og om muligt senest 72 timer efter opdagelsen (GDPR art. 33); ved høj risiko skal de registrerede underrettes (art. 34). Se [Datatilsynet: Anmeld sikkerhedsbrud](https://www.datatilsynet.dk/sikkerhedsbrud/anmeld-sikkerhedsbrud).
- **NIS2:** Væsentlige/essentielle enheder indberetter væsentlige hændelser til de digitale myndigheder med egne frister (tidlig varsling 24 timer, underretning 72 timer, slutrapport).
- **Datatilsynets "10 typiske brud"** ([datatilsynet.dk](https://www.datatilsynet.dk/regler-og-vejledning/behandlingssikkerhed/de-10-brud)): fejlsendte data, eksponerede beskyttede adresser, manglende sletning, ukrypterede tabte/beryttede enheder, for bred adgang på netværksdrev, kodefejl/dårligt design, data i skabeloner og ransomware. Godt supplement til diskussion af menneskelige fejl som hyppigste brudårsag.

## Evaluering

Evaluér på: præcision i adskillelsen af delpåstande, korrekt brug af guidens afsnit som dokumentation, kvalitet af korrektionerne, og prioriterings-argumentationen i pkt. 4.

## Kilde

Rigspolitiets Nationale Cyber Crime Center (NC3) & Dansk IT: *Virksomhedsguide – Forholdsregler ved brud på it-sikkerhedssystemer* (15 sider). Alle punktnumre henviser til guidens afsnit.
