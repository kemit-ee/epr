# Tehnilised ID-d skriptide jaoks

## Project ja repod

| Resurss | Node ID |
|---|---|
| Project #6 "Extended Producer Responsibility (EPR)" | `PVT_kwDOD4W7yc4Bm9Ob` |
| Repo `kemit-ee/epr` | `R_kgDOVIr_ZA` |
| Repo `kemit-ee/epr-nouded` | `R_kgDOVIsOcA` |

## Project #6 field ID-d

```
Status (built-in):   PVTSSF_lADOD4W7yc4Bm9ObzhlkCHs
Tüüp:                PVTSSF_lADOD4W7yc4Bm9ObzhlkEoA
Teema:               PVTSSF_lADOD4W7yc4Bm9ObzhlkEpo
Prioriteet:          PVTSSF_lADOD4W7yc4Bm9ObzhlkEtI
Domeen:              PVTSSF_lADOD4W7yc4Bm9ObzhlkEvw
BN seosed:           PVTF_lADOD4W7yc4Bm9ObzhlkEv0
KJ seosed:           PVTF_lADOD4W7yc4Bm9ObzhlkEv4
AR seosed:           PVTF_lADOD4W7yc4Bm9ObzhlkEwg
Algus:               PVTF_lADOD4W7yc4Bm9ObzhlkEw8
Sihtkuupäev:         PVTF_lADOD4W7yc4Bm9ObzhlkEx4
Äriomanik:           PVTSSF_lADOD4W7yc4Bm9ObzhlkEx8
Vaja ärilist otsust: PVTSSF_lADOD4W7yc4Bm9ObzhlkEyY
Risk:                PVTSSF_lADOD4W7yc4Bm9ObzhlkEz0
Allikas:             PVTF_lADOD4W7yc4Bm9ObzhlkE0Y
```

## Issue numbrite kaart (kemit-ee/epr)

| Numbri-vahemik | Teema | Mahud |
|---|---|---|
| #1–31 | Registreerimine ja autentimine | 3 Epic (#1, #14, #23), 7 Task, 20 Sub-task |
| #32–64 | Andmete esitamine ja valideerimine | 3 Epic (#32, #44, #54), 8 Task, 22 Sub-task |
| #65–95 | Järelevalve ja avalikustamine | 3 Epic (#65, #77, #86), 8 Task, 20 Sub-task |
| #96–103 | Pakendiaudit ja -aktsiis | 1 Epic (#96), 2 Task, 5 Sub-task |
| #104–120 | WEEE ja Patareid | 2 Epic (#104, #113), 4 Task, 11 Sub-task |

**Epic'ude number'id:** 1, 14, 23, 32, 44, 54, 65, 77, 86, 96, 104, 113
**Task'ide numbrid:** 2, 6, 10, 15, 19, 24, 28, 33, 37, 41, 45, 49, 55, 59, 62, 66, 70, 74, 78, 82, 87, 90, 93, 97, 101, 105, 109, 114, 118
**Ülejäänud 79** on Sub-task'id

## Nõuete issue numbrite kaart (kemit-ee/epr-nouded)

- Issue'd `#1–12` on esimene 12 näidet (BN-002..005, KJ-001..003, KJ-030, AR-001..003, AR-009)
- Issue'd `#13+` on järjestikku ülejäänud 303 nõuet (BN-id, siis KJ-d, siis AR-id)

Täpne mapping on tiitlis `[BN-xxx]` / `[KJ-xxx]` / `[AR-xxx]`. Programmaatiliselt saab mapping kokku panna järgmiselt:

```bash
gh issue list --repo kemit-ee/epr-nouded --state all --limit 500 \
  --json number,title --jq 'map({(.title | capture("\\[(?<id>[A-Z]+-\\d+[a-z]?)\\]").id): .number}) | add'
```

## Üldine muster: issue loomine Project'is

```graphql
mutation($repo: ID!, $title: String!, $body: String!) {
  createIssue(input: {repositoryId: $repo, title: $title, body: $body}) {
    issue { id number url }
  }
}

mutation($proj: ID!, $cid: ID!) {
  addProjectV2ItemById(input: {projectId: $proj, contentId: $cid}) { item { id } }
}

mutation($proj: ID!, $item: ID!, $field: ID!, $opt: String!) {
  updateProjectV2ItemFieldValue(input: {projectId: $proj, itemId: $item, fieldId: $field, value: {singleSelectOptionId: $opt}}) { projectV2Item { id } }
}

mutation($p: ID!, $c: ID!) {
  addSubIssue(input: {issueId: $p, subIssueId: $c}) { subIssue { id } }
}
```

## Hoiatus

**`updateProjectV2Field` + `singleSelectOptions` kaotab olemasolevate item'ide field-väärtuse.**

Kui lisad uue valiku `Teema` fieldi (nt uus teema), tee kõigepealt varukoopia praegustest väärtustest ja taasta need pärast ümber-defineerimist. Juhtus 2026-10-15 Teemade 4 ja 5 lisamise ajal.

Taastamise muster:

```python
# 1. Enne: fetch praegused Teema väärtused per item ID
# 2. Uuenda field options'id (sh uus valik)
# 3. Loop: iga item ID + Teema-nimi → set_single_select
```
