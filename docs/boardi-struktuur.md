# Boardi struktuur

**Board:** https://github.com/orgs/kemit-ee/projects/6

## Hierarhia

```
Teema (Project field)
  └── Epic (Issue, Tüüp = "Epic")
        └── Task (Issue sub-issue of Epic, Tüüp = "Task")
              └── Sub-task (Issue sub-issue of Task, Tüüp = "Sub-task")
```

Project field `Tüüp` eristab tasandid. GitHub native "Issue types" ei ole kasutuses (see on organisatsiooni-tasandi feature, mida me ei lülitanud sisse).

## Project fieldid (26 kokku)

**13 default** (Title, Assignees, Status, Labels, Linked PRs, Milestone, Repository, Reviewers, Parent issue, Sub-issues progress, Created, Updated, Closed).

**13 custom:**

| Field | Tüüp | Valikud |
|---|---|---|
| **Tüüp** | Single-select | Epic · Task · Sub-task |
| **Teema** | Single-select | 5 teemat |
| **Prioriteet** | Single-select | Kõrge · Keskmine · Madal |
| **Domeen** | Single-select | Pakend · WEEE · ELV · Patarei · Rehvid · Tekstiil · SUP · Üldine |
| **BN seosed** | Text | nt `BN-002, BN-003` |
| **KJ seosed** | Text | nt `KJ-001, KJ-002` |
| **AR seosed** | Text | nt `AR-001, AR-009` |
| **Algus** | Date | item'i algus-kuupäev |
| **Sihtkuupäev** | Date | item'i lõpu-kuupäev |
| **Äriomanik** | Single-select | KeMIT – ärianalüütik · KeMIT – projektijuht · RÜ – nõuete omanik · TVO esindaja · Määramata |
| **Vaja ärilist otsust** | Single-select | Jah · Ei |
| **Risk** | Single-select | Kõrge · Keskmine · Madal |
| **Allikas** | Text | nt `ELVR art 19; JäätS § 25` |

**Status valikud:** Backlog · Ready · In progress · Review · Blocked · Done.

## 7 vaadet

| # | Nimi | Layout | Filter | UI-seadistus (käsitsi) |
|---|---|---|---|---|
| 1 | Jälgitavuse tabel | TABLE | — | Group by Teema |
| 2 | Minu laud täna | TABLE | `assignee:@me,-status:Done` | Sort: Sihtkuupäev ↑ |
| 3 | Kanban | BOARD | `-status:Done` | Column by Status |
| 4 | Roadmap / Gantt | ROADMAP | — | Dates: Algus → Sihtkuupäev, Group by Teema |
| 5 | Prioriteet | TABLE | `prioriteet:Kõrge,-status:Done` | Sort: Sihtkuupäev ↑ |
| 6 | Domeen | TABLE | — | Group by Domeen |
| 7 | Äripoole otsused ootavad | TABLE | `"Vaja ärilist otsust":Jah,-status:Done` | Sort: Prioriteet, Sihtkuupäev |

> **NB:** Projects v2 API ei toeta programmaatiliselt järgmist: Group by, Sort by, Table-vaate veergude valikut, Roadmap-vaate date-axis'e mäppingut. Need **tuleb UI-s käsitsi seadistada** pärast skripti-põhist loomist.

## Kuupäevad

**Ei kasuta** GitHubi Milestones ega kvartali-põhiseid etappe.

`Algus` ja `Sihtkuupäev` on **item-tasandi date-fieldid**. Gantt vaade (Roadmap layout) joonistab need ribadeks. Kuupäevad on vahemikus **2026-10-20 → 2027-11-30**.

**Sub-task'ide kuupäevad** on jaotatud parent Task'i akna järgi järjestikku (N võrdset segmenti N sub-task'ile).

## Igapäevane kasutamine

Äripoole igapäevane kasutuse mall:

1. **"Äripoole otsused ootavad"** (vaade #7) — mis vajab äri otsust nüüd
2. **"Minu laud täna"** (vaade #2) — mida mina pean täna tegema
3. **Roadmap / Gantt** (vaade #4) — kuhu asjad liiguvad ja mis sõltub millest

Arendusepoolne igapäevane:
- **Kanban** (vaade #3) — status
- **Prioriteet** (vaade #5) — mis on kõige kriitilisem
