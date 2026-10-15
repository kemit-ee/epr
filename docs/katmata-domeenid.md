# Katmata domeenid ja kasutusjuhud

Alustasime 3 teemast ja laienesime 5-ni. Kokku 5 teemat katab 43 kasutusjuhtu 68-st, mis Excelis on. **25 kasutusjuhtu jääb välja** — need on järgmise skaleerimise etapi kandidaadid.

## Katmata KJ-d klastrite kaupa

| Klaster | KJ-d | Mahu-hinnang | Soovituslik teema-nimi |
|---|---|---|---|
| **ELV vertikaal** | KJ-041, KJ-042, KJ-043, KJ-044, KJ-045, KJ-046, KJ-047, KJ-048, KJ-049, KJ-050, KJ-070 | 11 KJ → ca 30–40 issue'd | "Sõidukite käitlemine (ELV)" |
| **Tekstiil** | KJ-058 | 1 KJ → ca 4 issue'd | eraldi teema "Tekstiil" või osana "WEEE ja Patareid" laiendusest |
| **SUP / Kalapüük / Tubakas** | KJ-059 | 1 KJ → ca 4 issue'd | "SUP ja eri-tooted" |
| **Pakendipass + Ringluspass** | KJ-052, KJ-067 | 2 KJ → ca 6 issue'd | lisada Teemasse 2 (PPWR / DPP) |
| **Süsteemihaldus** | KJ-033, KJ-035, KJ-053 | 3 KJ → ca 9 issue'd | "Süsteemihaldus ja migratsioonid" |
| **Finantsvastutus + modulatsioon** | KJ-039, KJ-062 | 2 KJ → ca 6 issue'd | lisada Teemasse 2 (tasude modulatsioon) |
| **Piiriülesed mehhanismid** | KJ-040, KJ-066 | 2 KJ → ca 6 issue'd | "Piiriülesed mehhanismid (TFS, kulude jaotus)" |
| **Kogumine ja DRS** | KJ-019, KJ-024, KJ-064 | 3 KJ → ca 9 issue'd | "Kogumine ja DRS" |
| **Käitlustõendid ja -kohad** | KJ-042, KJ-047, KJ-065 | — (osaliselt ELV all) | — |
| **Autoriseeringud + volitatud esindaja laiendid** | KJ-037 | 1 KJ → ca 3 issue'd | lisada Teemasse 1 |
| **Probleemtooted** | KJ-023 | 1 KJ → ca 3 issue'd | lisada Teemasse 2 |
| **Teavituste eelistused** | KJ-034 | 1 KJ → ca 3 issue'd | lisada Teemasse 1 (kasutajahalduse alla) |
| **Andmevahetus järelevalve-infosüsteemidega** | KJ-051 | 1 KJ → ca 3 issue'd | lisada Teemasse 3 |
| **Rehvide täispikk Epic** | KJ-057 (praegu ainult sub-task tasandil T2.1.2 all) | 1 KJ → ca 6 issue'd | laiendada eraldi Epic'iks "WEEE ja Patareid" teemas (lisada "Rehvid") |
| **Patareide KJ-032 täispikk** | KJ-032 (praegu ainult sub-task Patareide andmemudel) | 1 KJ → ca 6 issue'd | laiendada eraldi Epic'iks |

**Kokku skaleerimisel:** ca 100–120 lisa-issue'd.

## Prioriteedi-ettepanek

| Prioriteet | Klaster | Põhjendus |
|---|---|---|
| **Kõrge** | ELV vertikaal | 2000/53/EÜ asendamine ELVR-iga, suur regulatiivne surve |
| **Kõrge** | Süsteemihaldus | parameetrite muudatus ilma arendustööta on äri jaoks kriitiline (AR-010) |
| **Keskmine** | Piiriülesed mehhanismid | PPWR ja akumääruse horisontaalne nõue |
| **Keskmine** | SUP / Pakendipass | PPWR 2025/40 jõustumisega paralleelselt |
| **Madal** | Tekstiil | SUP-direktiivi laiendus, täpne ulatus veel ebaselge |

## Kuidas edasi lisada

1. **Lisa teema** `Teema` fieldi valikutesse (`updateProjectV2Field` + singleSelectOptions). **NB:** see lööb olemasolevatel item'itel Teema-väärtuse maha — valmista taastamise skript enne.
2. **Loo Epic'ud, Task'id, Sub-task'id** sarnaselt praeguste teemadega. Vt praegune Teema 5 (WEEE ja Patareid) kui näide, kuidas uus teema integreerida.
3. **Lisa kuupäevad** fieldidele. Hoia tulevikus (praegusest 1+ kuu edasi).
4. **Lingi nõudeid** `kemit-ee/epr-nouded` repoossist. KJ-numbri → issue-nr mapping on nõuete repo tiitlite kaudu (`[KJ-xxx] Nimi`).
