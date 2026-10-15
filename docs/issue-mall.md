# Issue body-mall

Repo-tasemel on `.github/ISSUE_TEMPLATE/` all kolm vormi: `epic.yml`, `task.yml`, `subtask.yml`. Need rakenduvad automaatselt uue issue loomisel UI-s.

Allpool täispikk muster, mis näitab, mis on igas issue'is olemas:

## Täispikk näide (Epic või Task tasand)

```markdown
## Taust ja seosed

**Parent Epic:** #<nr>   ← ainult Task'il
**Parent Task:** #<nr>   ← ainult Sub-task'il

**Ärinõuded (BN):**
- kemit-ee/epr-nouded#1 — BN-002
- kemit-ee/epr-nouded#2 — BN-003

**Kasutusjuhud (KJ):**
- kemit-ee/epr-nouded#5 — KJ-001

**Ärireeglid (AR):**
- kemit-ee/epr-nouded#9 — AR-001
- kemit-ee/epr-nouded#12 — AR-009

**Allikas:**
- ELVR art 18, art 19, Annex VIII
- JäätS § 25
- WEEE direktiiv 2012/19/EL art 16

## Mida tahame saavutada

<1–2 lauset konkreetset outcome'i — mitte "teostada see samm">

## Vastuvõtukriteeriumid

- [ ] Konkreetne kriteerium 1
- [ ] Konkreetne kriteerium 2
- [ ] Konkreetne kriteerium 3

## Vastuvõtutestid

- [ ] Nimega test 1
- [ ] Nimega test 2

## Riskid ja sõltuvused

<Reaalsed riskid: välissõltuvused, SLA, regulatsiooni muutused>

## Mittefunktsionaalsed nõuded   ← ainult Epic ja Task, mitte Sub-task

- **SLA (availability):** 99.9% ametliku töö-ajal (E-R 08:00–20:00)
- **Jõudlus:** UI < 2 sek, API p95 < 500ms
- **Turvalisus:** ISO/IEC 27001; TARA / eIDAS; rollipõhine ligipääs; audit log muudetamatu
- **Andmekaitse:** GDPR kohane
- **Säilitamine:** 10 aastat pärast lõpetamist
- + task-spetsiifilised NFR-id

## Avatud küsimused äripoolele

- [ ] Konkreetne küsimus, mis vajab äri otsust
```

## Reeglid

1. **ID-d ei ole pealkirjas.** `[Epic] Tootja ja TVO/TKO registreerimine` — jah. `[Epic] BN-002..005 Registreerimine` — ei. ID-d on fieldides (`BN seosed`, `KJ seosed`, `AR seosed`) ja "Taust ja seosed" sektsioonis.
2. **Viited üks reas, mitte komadega.** Boordipilt on parem, kui iga BN/KJ/AR on eraldi reas.
3. **"Mida tahame saavutada"** on konkreetne outcome, mitte "teostada see samm".
4. **"Mittefunktsionaalsed nõuded"** on ainult Epic ja Task tasandil (Sub-task on liiga detailne).

## Nõuete repo (kemit-ee/epr-nouded) issue-formaat

Nõude-tüüpi issue'd on erineva struktuuriga, sest nad sisaldavad Exceli algteksti:

**BN:**
```markdown
## Nõue (otse Excelist)
**Nimetus:** <nimi>
**Kirjeldus:** <täispikk kirjeldus>
**Allikas:** <õigusakti viide>
**Seotud KJ-d:** KJ-xxx, KJ-yyy
**Prioriteet:** Kõrge/Keskmine/Madal
```

**KJ:** sisaldab ka Põhivoogu, Alternatiivvooge, Osalejad, Eeltingimused, Järeltingimused.

**AR:** sisaldab reeglit tingimusena ("Kui X, siis Y").

AR-tüüpi issue puhul võib Allikas olla **klõpsatavad URL-id** (vt järgnev jaotis).

## Õigusakti-URL mustrid

### EL määrused (ELI, igavene)

```markdown
[Akumäärus (EL) 2023/1542](https://eur-lex.europa.eu/eli/reg/2023/1542/oj)
[PPWR (EL) 2025/40](https://eur-lex.europa.eu/eli/reg/2025/40/oj)
```

Muster: `https://eur-lex.europa.eu/eli/reg/<aasta>/<nr>/oj`

### EL direktiivid (ELI, igavene)

```markdown
[WEEE direktiiv 2012/19/EL](https://eur-lex.europa.eu/eli/dir/2012/19/oj)
[Raamdirektiiv 2008/98/EÜ](https://eur-lex.europa.eu/eli/dir/2008/98/oj)
```

Muster: `https://eur-lex.europa.eu/eli/dir/<aasta>/<nr>/oj`

### EL ettepanekud (COM)

```markdown
[ELVR](https://eur-lex.europa.eu/legal-content/ET/TXT/?uri=CELEX:52023PC0451) art 19 _(ettepanek COM(2023) 451)_
```

Muster: `https://eur-lex.europa.eu/legal-content/ET/TXT/?uri=CELEX:<CELEX>`

### Eesti seadused (Riigi Teataja, uusim redaktsioon)

```markdown
[PakS](https://www.riigiteataja.ee/akt/PakS)
[JäätS](https://www.riigiteataja.ee/akt/J%C3%A4%C3%A4tS)
[MKS](https://www.riigiteataja.ee/akt/MKS)
[HMS](https://www.riigiteataja.ee/akt/HMS)
```

Muster: `https://www.riigiteataja.ee/akt/<lühend>` (NB: `ä` tuleb URL-encoded `%C3%A4`-ks).

### Näide täispikkadest linkidest

Vt [kemit-ee/epr-nouded#12 (AR-009)](https://github.com/kemit-ee/epr-nouded/issues/12) — "Kordumatu registreering".
