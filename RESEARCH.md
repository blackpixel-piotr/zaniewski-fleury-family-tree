# Fleury – Zaniewski genealogy: research graph

> **How to use this file (for a human or for Claude):** this is the persistent state of the research.
> The graph is split into **NODES** (people and families), **EDGES** (relationships) and the **FRONTIER**
> (open branches to explore, in priority order). Each fact carries an evidence level and a source ID from
> the SOURCES list. To continue: pick the highest-priority `OPEN` item in FRONTIER, research it, then update
> its node, its edges, SOURCES and the LOG. Never delete a hypothesis; mark it `REJECTED` and say why.
>
> Visual tree (artifact): https://claude.ai/artifact/CFxPtWLV6bJ8avA3bZDVjN
>
> **Source of truth for the graph: `data/graph.json`** (served inside the artifact; working copy at `/home/claude/tree/data/graph.json`).
> This Markdown file is the research narrative, the FRONTIER and the LOG. Every node and edge change goes into graph.json first.
>
> graph.json schema:
> - `people[]`: `{id, name, sex, status, line, gen, dates, facts[]}`
>   - `status`: C | P | H | FAM | X (see the legend)
>   - `line`: fleury | zaniewski | inlaw | hyp | root
>   - `gen`: generation; Filip = 0, Piotr = 7, hypothetical parents of Filip = -1
>   - `facts[]`: `{t: text, s: status, src: [source IDs]}`. Facts with status H are shown as "possible branches / questions".
> - `edges[]`: `{type, from, to, status, facts[]}`
>   - `type`: parent_of | spouse_of | possible_parent_of | relative_of
>   - for parent_of, `from` is the parent; spouse_of is undirected
> - `sources{}`: `{S##: {t: title, u: url}}`
> - Deep link to a person: artifact URL + `#ID` (with `_` written as `-`), e.g. `#F1`, `#R-LudwikaF`
> Last updated: 2026-11-16 · Researcher: Piotr Zaniewski (with Claude)

---

## 0. Legend

| Tag | Meaning |
|---|---|
| `[C]` | **Confirmed**: stated by a primary or reputable published source |
| `[P]` | **Probable**: consistent secondary sources, not yet checked against a primary record |
| `[H]` | **Hypothesis**: a plausible lead with no proof |
| `[X]` | **Rejected**: disproved; the reason is given |
| `[FAM]` | Family oral tradition or Piotr's own knowledge |
| `S##` | Source ID (see section 4) |

Node IDs: `F#` = Fleury line, `Z#` = Zaniewski line, `X#` = in-law / other family, `H#` = hypothetical ancestor.

---

## 1. Direct line (root → Piotr), compact view

```
H?  (parents of Filip, unknown; see the FRONTIER, branch A)
│
F1  Filip (de) Fleury, 1745 Nancy – 1811 Warsaw          [C]
│   son
F2  Marcin (de) Fleury, b. c.1790                         [P]
│   son
F3  Józef Fleury, b. c.1830, Wilno official 1859–1890     [C]
├── F4  Stanisław Filibert Fleury (1858–1915)              [C]  (collateral, great-great-granduncle)
└── F5  NN Fleury (daughter of Józef)                      [P]  ← great-great-grandmother
     │   daughter
     X1  NN (niece of F4) ═══ married ═══ Z1 Feliks Zaniewski (1885–1947)   [C] marriage
                                           │ son
                                           Z2 Tadeusz Zaniewski             [C]
                                           │ son
                                           Z3 Marek Zaniewski (Zakopane)    [C][FAM]
                                           │ son
                                           Z4 Piotr Zaniewski               [FAM]
```

Generations from Piotr: Z3 = father, Z2 = grandfather, Z1/X1 = great-grandparents (pradziadkowie),
F5 = great-great-grandmother (praprababcia), F3 = 3× great-grandfather (praprapradziadek),
F2 = 4×, F1 = 5× (praprapraprapradziadek).

---

## 2. NODES

### F1: Filip (Philippe) (de) Fleury
- **Born** 1 May 1745, Nancy (Duchy of Lorraine, then ruled by Stanisław Leszczyński) `[C]` S20
- **Died** April 1811, Warsaw (recorded as "31 IV", which is impossible; probably 30 IV or 1 V) `[C]` S20
- **Buried** Stare Powązki, Warsaw, kwatera 10, miejsce 89, inventory no. 3174 `[C]` S21. The epitaph reads "ADIUTANT KRÓLA STANISŁAWA"; the monument was erected by his widow and son. `[C]` S20
- **Career** `[C]` S17: lieutenant (porucznik) 1770 → captain 1772 → royal flügeladiutant 1781 → colonel of the Crown army 1788 (source: Wyroki Trybunału Piotrkowskiego) → general-adjutant to Stanisław August. In the Sejm text of 1790 he is "major, adiutant Pana Prezydenta" (adjutant to the Marshal/President). S22
- **Ennobled** 9 December 1790 by the Great Sejm, act no. 226 "Nobilitacja osób wojskowych", "wraz z potomstwem" (with descendants), on condition of an oath of loyalty. `[C]` S22, S17 (Sigillata)
- **Arms**: "Fleury, herb własny" (own arms). The design is UNKNOWN. `[C]` S18
- **Marriages** `[P]` S20: (1) wife NN; (2) wife NN, c.1763–1828. The database says "married c.1770", which is impossible if she was born c.1763, so the marriage was more likely c.1785–1790. A 1826 marriage record from St John's parish, Warsaw, is cited (who it concerns is unclear).
- **Children**: one son, b. c.1790 (= F2?) `[P]` S20
- **Notes**: a commoner. A French noble would have received *indygenat*, not *nobilitacja*. Compare Jan-Bernard Fleury de Bachoue (X10), a French nobleman who got indygenat in 1768. S17. So the "de" was most likely self-styled.
- PSB biography exists: *Polski Słownik Biograficzny*, vol. 7, p. 37. Not yet read. S23

### F2: Marcin (de) Fleury
- b. c.1790 `[P]` S20, S24. Son of F1 `[P]` `[FAM]` S40. Settled in Wilno `[P]` S3, S5, S40.
- **Per Marek (S40)** `[FAM]`: a teacher of Polish; "after the uprising" he opened a craft workshop in the Warsaw market square, **Rynek no. 25** (probably Rynek Starego Miasta 25). He made furniture for the aristocracy and repaired upholstery in expensive furniture. Then he moved to Wilno.
- **Chronology check:** the family is already near Wilno by 1858 (F4 born at Papaje), and F3 is a Wilno official from 1859. So "after the January Uprising" (1863) cannot be right. The **November Uprising (1830–31)** fits: after it the Russians closed Warsaw University and many schools, and teachers lost their posts. Change of trade c.1831–1835, move to Wilno c.1840–1855 `[H]`.
- **Confirmed as F4's paternal grandfather**: Minakowski lists Marcin de Fleury as F4's "Sosa 4" (paternal grandfather) `[C]` S24. Resolves conflict F-c.
- **The family moved Warsaw → Wilno in the first half of the 19th century**; F3 was **born in Warsaw**; the family was registered in the **St Martin community of foreign-born Catholics, attached to St Anne's parish (Šv. Onos) in Wilno** `[C]` S43. → New lead C3.
- To verify: Warsaw address and trade directories of the 1830s–1840s (Rynek Starego Miasta 25); the Warsaw guild records of cabinetmakers and upholsterers (cech stolarzy/tapicerów) at APW.
- Conflict: S24 also lists a "Marcin de Fleury" as uncle/great-uncle of F4. Needs resolving.
- The Fleury family appears in the list of Wilno city nobility 1813–1902 `[C]` S25, which implies a nobility file at LVIA.

### F3: Józef Fleury
- b. c.1830 `[P]` S24. Leased the Papaje manor farm near Wilno; Wilno magistrate official 1859–1890 `[C]` S4, S5. Moved to Zarzecze (Wilno) in 1863 `[C]` S4.
- A "Józef Fleury (–1890)" is in the Bernardine Cemetery, Wilno index `[P]` S6. A "Maria Fleury (–1892)" is there too and could be his wife `[H]`.
- Wife: NN.

### F4: Stanisław Filibert Fleury (collateral)
- 22 Aug (3 Sep NS) 1858 Papaje – 21 Apr (4 May NS) 1915 Wilno; photographer and painter; studio at ul. Wielka 47; buried in the Bernardine Cemetery `[C]` S1, S2, S5
- Wife: Felicja née Andrukowicz `[C]` S1/S3. S24 dates her c.1857–1941 and the marriage "c.1900". That conflicts with Wacława's 1888 birth.
- Children `[C]` S1, S3: Witold, Henryk, Kazimierz, Czesława, Wacława (b. 28 IX 1888 Wilno – 1966 Sopot; painter and scoutmaster; preserved the archive). "Czesiula Fleury (1893–1895)" is in the Bernardine Cemetery index `[P]` S6.
- **Kazimierz Fleury**: por. piech. st. sp. (retired lieutenant), murdered in Kharkiv in 1940 (Katyń massacre) `[C]` S26. S24 gives a son 1902–1940 (ppor. 1924, por. 1932) `[P]`.
- Other Fleury murdered in Kharkiv: **Aleksander Fleury**, por. rez., 72 pp, merchant. Relationship unknown `[H]` S26.

### F5: NN Fleury, daughter of Józef, sister of F4
- Existence inferred from "Feliks married F4's niece (siostrzenica)" `[P]` S7. Her married surname = X1's maiden name. **KEY UNKNOWN.**

### X1: NN, wife of Feliks Zaniewski
- Daughter of F5, niece (siostrzenica) of F4 `[P]` S7. **KEY UNKNOWN: first name and maiden name.**

### Z1: Feliks Zaniewski
- 1885–1947 `[C]` S7. Photographer and zincographer, collaborator of F4 `[C]` S7, S8.
- Zakład Cynkograficzny, Wilno, ul. Wielka 3, operating from 1919 `[C]` S27. Plates for Jan Bułhak's albums (1933) `[C]` S10; postcards "Fot. i klisze F. Zaniewski" `[C]` S9.
- Visited the Święto Gór festival in Zakopane in 1935 `[C]` S7.
- Children: **Tadeusz** (Z2), **Zofia ("Zosia")**, photographed in Gdynia in 1934 `[C]` S7.
- Exhibition "Fotoromans Wileński Feliksa Zaniewskiego", Gdańska Galeria Fotografii MNG, opened 18 Dec 2005 `[C]` S7. Piotr's family attended `[FAM]`.
- Place of death and burial: UNKNOWN.

### Z2: Tadeusz Zaniewski
- Son of Z1; carried on the photography tradition `[C]` S8. Dates and birthplace UNKNOWN.

### Z3: Marek Zaniewski
- Son of Z2, lives in Zakopane; does 3-D photography; calls F4 his "pradziadek" (in the loose sense) `[C]` S8, S11. Piotr's father `[FAM]`.

### Z4: Piotr Zaniewski
- `[FAM]`

### Zaniewski: earlier generations (unknown)
- Candidate arms and branches (none proven for Z1):
  - Zaniewski h. Lubicz, signed the 1697 royal election for the Trakai voivodeship (close to Wilno) S13
  - Zaniewski h. **Prus**, in 19th-century Lithuania, Lida district: parishes Dziembrowo (1849), Nacza (Czepietuny manor), Raduń (Kozakowszczyzna, 1815), Szczuczyn (1826) S28. **The best geographic candidate.**
  - Also Korczak, Roch II (Pierzchała) S12; Zdań S14
- Bernardine Cemetery, Wilno: Bohdan Zaniewski (1905–1935), Julian Zaniewski (–1941). Relationship unknown `[H]` S6.

### Other / context nodes
- **X10: Jan-Bernard Fleury de Bachoue**: colonel of the royal army, French nobleman, Polish indygenat 1768; Aleksander (his line?), ppor. 1830 `[C]` S17. Possibly a relative or patron of F1 `[H]`.
- **Pierre Laute de Fleury (= Bénard)**: director of King Stanisław Leszczyński's court theatre in Nancy; father of the actor Abraham-Joseph Bénard "Fleury" (b. 26 X 1750, Chartres) `[C]` S30, S31. At Abraham-Joseph's birth he styled himself an officer of the Orléans Mint; "Laute de Fleury" is a name he gave himself `[C]` S31.
- **Rosset de Fleury (ducs de Fleury)**: André-Hercule de Rosset de Fleury (1715–1810), governor of Lorraine and Barrois (1737), governor of Nancy (1738), grand bailli of Nancy (1752) `[C]` S32. There is no Philippe b. 1745 among his legitimate children `[C]` S32.

---

## 3. EDGES (relationships) with confidence

| From | Relation | To | Level | Source |
|---|---|---|---|---|
| F1 | father of | F2 | [P] | S20, S24 |
| F2 | father of | F3 | [P] | S5 (great-grandson chain), S24 |
| F3 | father of | F4 | [C] | S4, S5 |
| F3 | father of | F5 | [P] | inferred from S7 |
| F5 | mother of | X1 | [P] | S7 ("siostrzenica") |
| X1 | wife of | Z1 | [C] | S7 |
| Z1 | father of | Z2 | [C] | S8 |
| Z1 | father of | Zofia | [C] | S7 |
| Z2 | father of | Z3 | [C] | S8 |
| Z3 | father of | Z4 | [FAM] | Piotr |
| F4 | father of | Kazimierz (1902?–1940) | [C]/[P] | S26, S24 |
| F1 | ? relative of | X10 Fleury de Bachoue | [H] | – |
| F1 | ? son of | Pierre Laute de Fleury / Bénard family | [H] | see A2 |

**Conflict to resolve:** S8 calls F4 Marek's "pradziadek" (great-grandfather). If that were literal, X1 would be F4's daughter, not his niece. S7 (the exhibition notes) says "niece". The tree currently follows S7. The deciding evidence would be X1's baptism or marriage record, or Tadeusz's birth record.

---

## 4. SOURCES

| ID | Source | URL |
|---|---|---|
| S1 | Wikipedia (pl): Stanisław Filibert Fleury | https://pl.wikipedia.org/wiki/Stanis%C5%82aw_Filibert_Fleury |
| S2 | VLE (Lithuanian encyclopedia): S. F. Fleury | https://www.vle.lt/straipsnis/stanislaw-filibert-fleury/ |
| S3 | Gdańsk Strefa: Wacława Fleury & Antonina Świdzińska | https://www.gdanskstrefa.com/waclawa-fleury-antonina-swidzinska-harcmistrzynie-wilno/ |
| S4 | Tygodnik Wileńszczyzny: Papaje | http://www.tygodnik.lt/202044/bliska2.html |
| S5 | Kurier Wileński (2017): Fleury | https://kurierwilenski.lt/2017/02/11/fleury-jedna-z-najbarwniejszych-postaci-dawnego-wilna/ |
| S6 | Bernardine Cemetery, Wilno: name index | https://genealogia.okiem.pl/artykul/21021/cmentarz-bernardynski-wilno-litwa-spis |
| S7 | Fotopolis: "Fotoromans Wileński Feliksa Zaniewskiego" (2005) | https://www.fotopolis.pl/newsy-sprzetowe/wydarzenia/3330-wystawa-fotoromans-wilenski-felika-zaniewskiego |
| S8 | Watra (2011): Prezentacje w trójwymiarze | https://www.watra.pl/zakopane/kultura/2011/07/15/prezentacje-w-trojwymiarze |
| S9 | Europeana: postcard by F. Zaniewski | https://www.europeana.eu/en/item/2021803/LIMIS_827360577 |
| S10 | Polish Photobooks: Bułhak, Przez Ponary do Trok (1933) | https://polishphotobooks.com/en/0023-wedrowki-fotografa-w-slowie-i-obrazie-iii-przez-ponary-do-trok/ |
| S11 | Filharmonia Szczecin: Karłowicz exhibition note | https://filharmonia.szczecin.pl/wydarzenia/614-Wernisaz_Mieczyslaw_Karlowicz_Tatrzanskie |
| S12 | Gajl armorial, letter Z | https://ornatowski.com/wykazy-nazwisk/herby-szlacheckie-rzeczypospolitej-obojga-narodow/z-herby-szlacheckie-rzeczypospolitej-obojga-narodow/ |
| S13 | Genealogia Polska: Zaniewski | https://polishgenealogy1.blogspot.com/2018/07/zaniewski.html |
| S14 | Herbarz szlachty białoruskiej, vol. 7 | https://lyczkowski.net/pl/herbarz/szlachty-litewskiej/tom-7 |
| S15 | historycy.org: Lubicz | http://historycy.org/bez_grafik/index.php/t23561.html |
| S17 | Uruski, *Rodzina. Herbarz szlachty polskiej*, vol. IV (F) | https://onebid.no/no/papers/Rodzina-herbarz-szlachty-polskiej/Tom-IV-F |
| S18 | Gajl armorial, letter F ("Fleury h. własny") | https://przodek.pl/genealogia/tadeusz-gajl-herby-szlacheckie-rzeczypospolitej-obojga-narodow-f |
| S20 | Minakowski, Wielka Genealogia: Filip de Fleury | https://www.sejm-wielki.pl/b/psb.5719.4 |
| S21 | Minakowski: Stare Powązki, kwatera 10 | https://www.sejm-wielki.pl/s/cmentarze.php?kw=10 |
| S22 | Dziennik Sejmu Wielkiego, 9 XII 1790, act 226 | https://www.sejm-wielki.pl/dziennik/dzien.php?data=1790-12-09 |
| S23 | PSB vol. 7 (1948–58), "Firlej – Frieman" part, at RCIN | https://rcin.org.pl/ihpan/dlibra/publication/14489/edition/2438 |
| S24 | Minakowski: Stanisław Filibert Fleury | https://www.sejm-wielki.pl/b/psb.5719.1 |
| S25 | Malewski: list of Wilno city nobility 1813–1902 | https://genealogia.lt/pdfs/szlachta_wilenska.pdf |
| S26 | Katyń victims murdered in Kharkiv (list) | https://www.wikiwand.com/pl/Ofiary_zbrodni_katy%C5%84skiej_%E2%80%93_zamordowani_w_Charkowie |
| S27 | Księga adresowa m. Wilna 1932 (archive.org OCR) | https://archive.org/stream/VilnaCollectionPolishResources/1932.%20Ksi%C4%99ga%20Adresowa%20m.%20Wilna%20%20%20wile%C5%84ski%20kalendarz%20informacyjny_djvu.txt |
| S28 | Malewski, *Rodziny szlacheckie na Litwie w XIX w.* (PDF; Zaniewski h. Prus at offset ~700k chars) | https://www.genealogia.lt/pdfs/rodziny_szlacheckie.pdf |
| S29 | Dziennik Sejmu Wielkiego: person index | https://www.sejm-wielki.pl/dziennik/osoba.php?o=psb.5719.4 |
| S30 | Comédie-Française: Abraham-Joseph Bénard dit Fleury | https://www.comedie-francaise.fr/en/artist/fleury-abraham |
| S31 | Geneanet (tinagaquer): A.-J. Bénard, note on his father | https://gw.geneanet.org/tinagaquer?n=benard&oc=&p=abraham+joseph |
| S32 | Études héraultaises (1982): *Les héritiers du Cardinal de Fleury* | https://www.etudesheraultaises.fr/wp-content/uploads/1982-3-02-les-heritiers-du-cardinal-de-fleury.pdf |
| S33 | Archives municipales de Nancy: parish registers catalogue | https://recherche-archives.nancy.fr/ |
| S34 | Archives départementales 54: online registers | https://archivesenligne.meurthe-et-moselle.fr/archives-en-ligne |
| S35 | Cahiers lituaniens: cadets of Lunéville | https://www.cahiers-lituaniens.org/PARENT-cadets-Luneville-n-14-2015.pdf |
| S36 | Orbis Linguarum 59/2025: Poles in French hussar regiments / cadets of Lunéville | https://www.orbis-linguarum.pl/articles/59/09_toth.pdf |
| S43 | 15min.lt, G. Kajėnas: "Fleury fotografinės klajonės" (based on J. Gudaitė's LNM album, 2007) | https://www.15min.lt/media-pasakojimai/vilnius-ir-jo-apylinkes-daugiau-nei-pries-simtmeti-fleury-fotografines-klajones-1240 |
| S44 | J. Gudaitė (ed.), *Stanislaw Filibert Fleury. Fotografijos*, Lietuvos nacionalinis muziejus, 2007 (album; probably has the family background) | book |
| S45 | Myszkowscy family site, Warsaw lines: Ludwika Fleury b. 1779 Lyon | https://www.myszkowscy.pl/r7.html |
| S46 | lt.wikipedia: Vaclava Fleri (Wacława Fleury), d. 10 V 1983 Sopot | https://lt.wikipedia.org/wiki/Vaclava_Fleri |
| S47 | Vilnius University Library: S. F. Fleury biography | https://biblioteka.vu.lt/e.parodos/vilnius-fotografijose/izanga_fleury_en.htm |
| S40 | Marek Zaniewski (Z3), message to Piotr, 17 XI 2026: family knowledge from memory and a hand-drawn tree | `[FAM]` |
| S41 | Online Fleury family tree made by someone from Wilno, found by Marek. **URL to get from Marek** | ? |
| S42 | Family archive held by Marek: birth, marriage and notarial records, **in Russian** | `[FAM]`, untranslated |

---

## 5. FRONTIER (open branches, in priority order)

### Branch A: Before 1745 (Filip's parents)
- **A1. Filip's baptism, Nancy, ~1 May 1745.** `OPEN`, highest priority.
  - Nancy parishes in 1745: Notre-Dame, Saint-Epvre, Saint-Sébastien, Saint-Nicolas, Saint-Roch, Saint-Vincent-Saint-Fiacre, Saint-Pierre (S33).
  - Images are online at AD54 (S34). **Blocked for Claude**: the site returns "forbidden" to the cloud browser, and the main AD54 site was shut down on 21 Oct 2026 pending a new one. Piotr must open it himself, or send screenshots for Claude to read.
  - Shortcuts: (a) the Archives municipales de Nancy hold a **name index of Notre-Dame births 1729–1749** (Fonds Tschitschmann, 370 Z 80) and baptism tables for Saint-Epvre 1714–1761 (S33). (b) Geneanet and FamilySearch indexes.
  - A Latin entry would read something like "Philippus, filius legitimus ... Fleury et ..., baptizatus est die prima / secunda maii 1745". It names the father, the mother's maiden name and the godparents. Godparents from the court would be a huge clue.
- **A2. Hypothesis: the Bénard "de Fleury" theatre family.** `[H]` `OPEN`
  - Why it's plausible: Pierre "Laute de Fleury" ran Leszczyński's court theatre in Nancy; he styled himself "de Fleury" without being noble; the family travelled around Lorraine and Champagne (S30, S31). That would fit Filip being a commoner with a self-styled "de".
  - Against: the actor son was born in Chartres in 1750, and in 1750 the father called himself an officer of the Orléans Mint, so the family may not have been in Nancy in 1745.
  - Test: find Pierre Bénard's children (Geneanet tree S31, d'Alméras' 1903 notes to the *Mémoires de Fleury*). Is there a Philippe born in 1745? Do the memoirs mention a brother in Poland?
- **A3. Hypothesis: born into the household or circle of the Duc de Fleury, governor of Nancy (1738–).** `[H]` low. No legitimate Philippe born in 1745 (S32). An illegitimate child or a servant's son taking the name is speculative. Don't pursue unless A1 points there.
- **A4. Hypothesis: a cadet of Lunéville, then service in Poland.** `[H]` `OPEN`, medium.
  - Stanisław Leszczyński's École des cadets-gentilshommes (1737–1766) trained many future officers for Poland (S35, S36). The roll of 564 cadets is in Arthur Benoît, *L'École des cadets-gentilshommes du roi de Pologne* (Lunéville, 1865), probably on Gallica. Check it for "Fleury".
  - Against: cadets had to be noble; Filip needed ennobling in 1790.
- **A5. Lorraine commoner families named Fleury.** `OPEN`: Geneanet search for FLEURY in Meurthe-et-Moselle, 1700–1760.

### Branch B: Filip in Poland (1765–1811)
- **B1. PSB vol. 7, p. 37**: read the Fleury entry or entries (S23). RCIN blocks automated fetching; open it manually. `OPEN`
- **B2. AGAD, Sigillata 1790 and Metryka Koronna**: the nobility diploma and the description of the arms. `OPEN`
- **B3. Volumina Legum IX (1790)**: the printed act (names only). `OPEN`
- **B4. Warsaw, St John's parish**: Filip's marriages, his death (1811), his widow's death (c.1828), Marcin's baptism (c.1790). Geneteka (geneteka.genealodzy.pl) indexes Warsaw parishes. `OPEN`
- **B5. Powązki, kw. 10 m. 89**: photograph the gravestone (arms? full epitaph? wife's name?). The City of Warsaw's cemetery inventory may have photos. `OPEN`
- **B6. Minakowski, Wielka Genealogia (paid)**: reveals the hidden names of F1's wives, F2 and F3's wives, and others. `OPEN`, cheap, high yield.
- **B7. X10 Fleury de Bachoue**: is he connected to Filip (patron, relative)? `OPEN`

### Branch C: Warsaw → Wilno (F2, F3)
- **C1. LVIA Vilnius, fond 391 (Wilno Noble Deputation)**: the Fleury nobility file (Wilno 1813–1902, S25). It would prove the F1 → F2 → F3 chain and list children, possibly including F5. `OPEN`, high.
- **C2. Wilno parish registers on epaveldas.lt**: the children of Józef Fleury, c.1855–1870, to find F5 and her marriage. `OPEN`, high.

### Branch G: Family archive (NEW, highest yield)
- **G1. Translate Marek's Russian documents (S42).** Births, marriages, notarial acts. `OPEN`, **TOP PRIORITY**. Marek photographs them page by page; Claude transcribes, translates into Polish and updates the nodes. Notarial acts often list heirs, so they could show F5 → X1 → Z1 directly.
- **G2. Get the URL of the Wilno-made online Fleury tree (S41).** `OPEN`. Compare it with this graph and resolve the conflicts.
- **G3. Photograph Marek's hand-drawn tree.** `OPEN`
- **G4. Marcin's Warsaw workshop, Rynek 25** (see F2). `OPEN`

### Branch C (new items)
- **C3. Wilno, St Anne's parish (Šv. Onos) / St Martin community of foreign-born Catholics** (S43). Its metrical books (LVIA fond 604 = Wilno consistory copies; also epaveldas.lt) should hold the Fleury baptisms, marriages and deaths from c.1830 onward: F3's marriage, the children including F5, and the deaths of F2 and Marcin's wife. `OPEN`, **HIGH**.
- **C4. J. Gudaitė's 2007 LNM album (S44)**: probably the "tree made by someone from Wilno" that Marek saw, or its source. Ask the National Museum of Lithuania / check Polish libraries (NUKAT). `OPEN`

### Branch B (new items)
- **B8. Ludwika Fleury, b. 1779 Lyon, daughter of Józef Fleury and Anna Ludwika; married Józef Szulke; d. 6 III 1849 Warsaw (St Alexander's parish); the record notes the address Rynek Starego Miasta 42** (S45). Another French Fleury family in Warsaw, in the same market square where Marcin later had his workshop (no. 25, per S40). Relationship to F1 unknown `[H]`: a brother's family, or a different family. Check on Geneteka: Warsaw, surname Fleury, 1790–1850. `OPEN`

### Branch F (new items)
- **F-d.** Wacława Fleury's death: 1966 (S3) vs 10 V 1983, Sopot (S46). `OPEN`
- **F-e.** S. F. Fleury's birth: 1858 (most sources) vs 1861 (S47, and the "Stanisław Fleury (1861–" entry in S6). `OPEN`

### Branch D: Zaniewski
- **D1. Ask Marek (Z3)** `[FAM]`: X1's name and maiden name; Tadeusz's birth date and place; where Feliks died and is buried; family papers; any signet ring or seal; the 2005 exhibition catalogue. `OPEN`, **cheapest and highest yield.**
- **D2. Feliks's parents**: his 1885 birth record (Wilno or the Lida district?). `OPEN`
- **D3. Zaniewski h. Prus, Lida district (S28)**: test whether Feliks's line comes from Dziembrowo, Nacza, Raduń or Szczuczyn. `OPEN`
- **D4. LVIA fond 391**: a Zaniewski nobility file, if any. `OPEN`
- **D5. Bohdan (1905–1935) and Julian (–1941) Zaniewski**, Bernardine Cemetery: relatives? `OPEN`
- **D6. MNG / Gdańska Galeria Fotografii**: 2005 catalogue and lender records. `OPEN`

### Branch E: Heirlooms
- **E1. Two paintings attributed to Stanisław Leszczyński** `[FAM]`, passed down through the generations. `OPEN`. Piotr will send photos of the front, the back (labels, stamps, inscriptions), signatures and dimensions.
  - Why it matters: Filip was born in Nancy in 1745 during Leszczyński's reign; a court gift would back up a link between the family and the court (A2/A4).
  - Caution: Leszczyński isn't documented as a painter. The attribution needs an expert (Musée Lorrain, Nancy; MNW; MNK).
  - Also check: how the paintings reached the Zaniewskis. They came through the Fleury daughter (F5 → X1)? Or the Zaniewski side?
- **E2. Signet ring, seals, engraved silver**: ask the family. `OPEN`

### Branch F: Collateral (lower priority)
- **F-a.** Aleksander Fleury (Kharkiv 1940): his relationship to F4. `OPEN`
- **F-b.** The Wacława birth-year (1888) vs. marriage "c.1900" conflict in S24. `OPEN`
- **F-c.** Marcin as grandfather vs. uncle of F4 (S24). `OPEN`

---

## 6. REJECTED / closed

- `[X]` **The Napoleonic straggler legend** (a Fleury left behind in Wilno in 1812): Filip was serving in Poland from 1770 (S17), and his descendants were registered as Wilno nobility from 1813 (S25).
- `[X]` **That Filip was a recognised French noble**: he was ennobled in 1790 rather than given indygenat (S17, S22).
- `[X]` **Filip as a legitimate son of the Rosset de Fleury dukes**: there is no Philippe b. 1745 in that family (S32).
- `[X]` **That Piotr inherits the Fleury arms**: Polish arms passed in the male line only; Piotr descends through a Fleury daughter (F5). His arms, if any, are the Zaniewski ones.

---

## 7. Research log

| Date | What was done | Result |
|---|---|---|
| 2026-11-16 | Started from S1 (S. F. Fleury) | F1–F4 outline |
| 2026-11-16 | Searched "Zaniewski Fleury" | Z1 Feliks = husband of F4's niece (S7); Z2, Z3 (S8) |
| 2026-11-16 | Heraldry search | Zaniewski: several arms (S12–S14); Fleury: nothing at first |
| 2026-11-16 | French sources | Nothing direct |
| 2026-11-16 | Uruski | F1's career and 1790 ennoblement (S17) |
| 2026-11-16 | Deep dig | Gajl "Fleury h. własny" (S18); Minakowski: F1 b. 1 V 1745 Nancy, d. 1811 Warsaw, Powązki grave (S20, S21); Sejm act 226 (S22); Kazimierz Fleury, Katyń (S26); Feliks's workshop at Wielka 3 since 1919 (S27); Zaniewski h. Prus in the Lida district (S28) |
| 2026-11-16 | Pre-1745: Nancy | Hypotheses A2–A4 identified; parish list (S33); AD54 online registers blocked for automated access (S34) |
| 2026-11-16 | Piotr: has two paintings attributed to Leszczyński | Added E1 |
| 2026-11-16 | AD54 online registers | Blocked (forbidden) for both Claude and Piotr's iPhone; email drafted to Nancy municipal archives and AD54 asking for the 1745 baptism |
| 2026-11-17 | Marek's message (S40) | Confirms F1 (Nancy 1745 – Warsaw 1811, flügeladiutant); F2 Marcin: Polish teacher, then a furniture and upholstery workshop at Rynek 25 in Warsaw, then Wilno; F3 Józef: Wilno magistrate official. Marek has Russian documents (S42) and knows of an online tree (S41) → Branch G |
| 2026-11-17 | **Geneteka (Warsaw) and the Wrocław grave search** | **Marcin baptised 1782, St Andrew's, father Filip** (resolves the Szkoła Rycerska conflict). Filip's death record 1811 (age 65). 2nd wife = **Regina Petrasch** (d. 1828; remarried Łapiński in 1826). Half-brother **Józef Andrzej** (1799–1824), **godfather Prince Józef Poniatowski**. Candidate 1st wife: Ludwika Fleury (d. 1817, age 56, widow, children Marcin, Ludwika, Karolina Łozińska): H. **Feliks's grave: Osobowice, Wrocław, plot 67/1/1, d. 30 VI 1947** (the family's "early 50s" is wrong); burial record 1965 (a transfer?); the grave lease expired in 1985. Czesława not found in the municipal database. Film: "Mistrz scen rodzajowych" (TVP3 Gdańsk 2018). Next: read the 1782 and 1817 scans (mothers); ask ZCK Wrocław about the grave and Czesława |
| 2026-11-17 | Marek: Marcin was Filip's son and graduated from the Szkoła Rycerska (Corps of Cadets) in Warsaw | Date conflict: the school closed 30 XI 1794 (S59). Either Marcin was born c.1775–82 (Filip's 1st marriage?), not c.1790, or the school was really the Liceum Warszawskie (1804–31, later in the same Kazimierz Palace). Check the cadet lists: K. Mrozowska, *Szkoła Rycerska…* (1961), index of names; Kajety KK vol. 2 (S60); AGAD/MWP records. If he was a cadet, the cadet register gives his age and father → proof of the F1→F2 link |
| 2026-11-17 | Marek: Tadeusz was a sniper (strzelec wyborowy) in WWII | Added to Z2 (FAM). Unit unknown: AK Okręg Wilno (Ostra Brama 1944)? LWP? Search: AK Wilno database (S55), CAW Rembertów personnel files, IPN, Arolsen; Zakopane graves (Grobonet S57, Nowy Cmentarz). The IPN "Tadeusz Zaniewski 'Dąb'" b. 1925 Łomża is someone else (S56) |
| 2026-11-17 | Marek: Tadeusz Zaniewski b. 1 IV 1924 Wilno, d. 29 IV 1994 Zakopane | Z2 dates filled in (FAM). The marriage Z1 × X1 was before 1924. Next: Tadeusz's baptism in Wilno in 1924 (Russian or Polish? Polish administration, so the record is in Polish/Latin), grave in Zakopane, the route after 1945 |
| 2026-11-17 | **Marek: Feliks's wife = Czesława Wygonowska h. Paprzyca, daughter of Jan Wygonowski and Wacława Fleury** | Key missing link closed (as family knowledge, FAM). F5 = Wacława z Fleurych Wygonowska; F5h = Jan Wygonowski h. Paprzyca; X1 = Czesława z Wygonowskich Zaniewska. The Watra "pradziadek" version is downgraded to X. New line: Wygonowscy h. Paprzyca (Podlasie / woj. brzeskie litewskie; S49–S52). Next: Wacława and Jan's marriage record (Wilno, St Anne's?), Czesława's baptism, Jan Wygonowski's parents |
| 2026-11-17 | Followed up Marek's leads online | Marcin = F4's paternal grandfather (S24); the family moved Warsaw → Wilno in the first half of the 19th c.; Józef was born in Warsaw; the Wilno parish was St Anne / St Martin community (S43); the 2007 LNM album (S44) is a likely candidate for the online tree; Ludwika Fleury (Lyon 1779 – Warsaw 1849), Rynek Starego Miasta 42 (S45); date conflicts F-d, F-e. Online tree S41 not found yet |

---

## 8. Next session: start here

0. **G1/G2**: Marek's Russian documents (photos) and the URL of the Wilno online tree.
1. **D1**: Piotr asks Marek: X1's name, Tadeusz's dates, family papers, the paintings' history. Fill the answers into X1, Z2 and E1.
2. **A1**: Piotr opens AD54 (S34), Nancy, 1745. Look in Saint-Epvre first (the court parish), then Notre-Dame and Saint-Sébastien, around 1–2 May. Screenshot the entry for Claude to transcribe.
3. **B6**: optionally, a month of Minakowski's subscription to reveal hidden names.
4. **E1**: photos of the paintings.
5. Claude: check Gallica for Benoît (1865), the cadets list (A4), and for d'Alméras' edition of the *Mémoires de Fleury* (A2).

### Document 1 from Marek (2026-11-17): Józef's will, 1890 (S76)
- Józef = "Osip Martynovich Fleury", son of Marcin (confirmed). Legal status: "townsman of the city of Warsaw" (meshchanin), not nobleman.
- Will dated 11 II 1890 at his house on Połocka St., Wilno. He was ill, so someone signed for him. The court (Vilna Circuit Court) approved the will of "the deceased" on 3/4 XII 1890, so he died in 1890.
- Wife: **Maria Antonovna** (daughter of Antoni). She is the sole heir: a wooden house on Połocka on land of the Holy Spirit monastery, which she leased (notary Bogdanov, 30 XII 1887).
- Leads: (a) the will was published in "Сенатские объявления" (Senate notices), 1890–91, which may also be scanned; (b) the Wilno notary books (Nieiełow 1889–90, Bogdanov 1887) are in the Lithuanian State Historical Archives (LVIA); (c) the Warsaw population register for "мещанин Варшавы" Fleury; (d) Maria's maiden name: look in Wilno marriage records c. 1855–57 (Józef × Maria, daughter of Antoni).

### Documents 2–4 from Marek (2026-11-17): S77 marriage 1884, S78 baptism 1885, S79 Maria's will 1891
- The Wygonowski bride is **Helena** Fleury (21 in 1884), not "Wacława" as the family remembered: daughter of the noble Józef and **Maria née Bohdanowicz**. She married Jan (Iwan) Wygonowski (27, Evangelical-Reformed, mother Dorota née ?) on 12 VII 1884 at the Antokol church; Stanisław Fleury was a witness.
- **Czesława born 27 V 1885**, Połocka St., Wilno; baptised 8 VII 1885 at the Bernardine church; godparents Stanisław Fleury and Kazimiera Dziewicka?.
- Maria's will (9 X 1891): the Połocka house goes to her daughter Helena Wygonowska; Maria died before 1893.
- Note: the notarial deeds call the family "meshchane" (townsfolk), the church records call them "dvoriane" (nobility).
- Next: Wilno Bernardine parish books in LVIA (fond 604) for births of Józef's children (c. 1855–65) and Józef's marriage to Maria Bohdanowicz; the Evangelical-Reformed parish in Wilno for Jan Wygonowski (b. c. 1857, mother Dorota).

### Branch W – Wygonowscy (Geneteka Litwa search, 2026-11-17)
- **Marriage of Feliks Zaniewski × Czesława Wygonowska: 1918, Wilno, Bernardine parish (SS. Francis & Bernard), record 2** (S80; scan on FamilySearch, needs a free login). The record should give both sets of parents, so it would identify Feliks's parents and confirm Jan and Helena.
- Jerzy Wygonowski, son of Jan, died as a child in 1914 in the same parish (S81): H, possibly Czesława's brother.
- Other Wilno noble Wygonowscy of the same generation (possible brothers or cousins of Jan): Tadeusz × Florentyna Gerold/Herold (children 1888 Elżbieta, 1889 Maria †, 1890 Czesława, 1898 Tadeusz; St Spirit / SS Peter & Paul); Bolesław Piotr, son of Józef and Teresa, married Aniela Doboszyńska in 1889 (St Teresa); Władysław × Konstancja Urońska (1894, 1901). The Troki/Giedrojcie Wygonowscy are Catholic peasant or petty-gentry lines, probably unrelated.
- Jan was Calvinist, so his own baptism (c. 1857) should be in the Wilno Evangelical-Reformed register (LVIA f. 605? / FamilySearch "Lithuania, Evangelical Reformed"), not in the Catholic indexes. Mother Dorota.
- Not indexed online yet: the births of Helena and Jan's other children (Bernardine parish 1885–1900).

### Branch M – Muzeum Narodowe w Gdańsku (Marek, 2026-11-17)
- Marek confirms: the great-grandmother was HELENA (he got the name wrong; "Wacława" is rejected).
- The National Museum in Gdańsk holds family documents: the design (plans) of the house on Połocka St. and memorabilia of Stanisław Filibert Fleury. This probably ties in with the 2005 photo exhibition in Gdańsk.
- To do: ask the museum (Photography / Archive department) for an inventory of the Fleury deposit or gift and digital copies. The house plan may give the address number, the plot and the year of construction.

### Pre-1745 plan (2026-11-17)
- Filip's 1811 death record has been read: it does not name his parents. It gives his widow Regina née Petrasz and his son Józef, aged 12. He may be "former colonel? of the Polish Army" (uncertain reading).
- KEY DOCUMENT: Filip's baptism, Nancy, 1 V 1745 (Philippe-Jacques Fleury). Nancy parishes: St-Epvre, St-Sébastien, Notre-Dame, St-Roch, St-Nicolas, St-Pierre. Online: archives.meurthe-et-moselle.fr (blocked for us and for Piotr's iPhone, possibly geo-blocked, so try a French VPN), Geneanet, Filae, and the Cercle Généalogique de Nancy / UGEL index.
- Then: his parents' marriage (Nancy c. 1730–45), then their baptisms, then back into the 1600s (Lorraine registers are good back to c. 1600).
- Polish side that may give his parents' names: Filip's 1st marriage in Warsaw (c. 1780, St Andrew's?), his 1790 ennoblement entry (Metryka Koronna / Sigillata, AGAD), and Marcin's baptism 1782 (scan file 404-405).

### Branch P – the paintings and the Leszczyński angle (Marek's mail, 2026-11-17)
- Provenance (family account): Feliks cut the 2 paintings from their frames during the 1946 repatriation from Wilno and took them to Wrocław; Tadeusz brought them to Zakopane; in 2002 they went to the Tatra Museum conservator; in 2003 the Kraków Academy of Fine Arts (prof. Marian Paciorek) analysed pigments and IR/UV and judged them 17th c., in the manner of Ruisdael; later dr Dorota Juszczak (Łazienki) judged them 18th c., by a provincial painter.
- Documentary chain: Maria's 1891 will leaves ALL movables to Helena, so the paintings may have come via Józef → Maria → Helena → Czesława.
- Solid historical angle: Stanisław Leszczyński was Duke of Lorraine, with courts at Nancy and Lunéville, 1737–1766. Filip was born in Nancy in 1745, so his family could have served the ducal court. To check: the Lorraine ducal household records (AD54 series B), and Lorraine/Lunéville court painters (provincial 18th c. fits the Juszczak opinion).
- Marek's hidden-symbol reading (Wissembourg, Wasigenstein, Zweibrücken) is his interpretation, unverified; treat it as H.
- Marek's claim that "Maria was Helena's stepmother" contradicts S77 (Helena is the legitimate daughter of Józef and Maria Bohdanowicz). Perhaps Maria was Stanisław's stepmother instead.
- Powązki epitaph per Marek: "Bywszy Adiutant Króla Stanisława … Pozostała Żona z Synem" (FAM).
- Claude's own to-do: search the AGAD Metryka Koronna / Sigillata for the 1790 ennoblement of Fleury (szukajwarchiwach.gov.pl); the Powązki grave in the Stare Powązki database.

### Branch F-Z – Feliks's firm (2026-11-17)
- S84, V. Juodakis, "Iš cinkografijos istorijos Lietuvoje" (Knygotyra): Feliks was an apprentice retoucher with A. Daukša c. 1900, then worked for **Stanisław Fleury from late 1903**. In 1905 he did the retouching and etching for the first Wilno zinc plates. **After Stanisław died (1915) he bought the pavilion and zincography from the widow**, closed the photo studio and moved the zincography to Gorkio g. 25 (Soviet street name; Wielka/Didžioji?, courtyard of Wysocki's pharmacy). He was the "king of the business" in Wilno; the firm ran 1905–1915–1940. He left for Poland in 1944, reopened a zincography there, and passed it to his SON. Which son? Tadeusz, or Z1c2? Was it in Wrocław?
- This explains how Feliks met Czesława (Stanisław's niece): marriage 1918.
- Marek: the firm also mass-produced postcards, rotogravure and colour plates for albums and encyclopedias.
- Marek: the "stepmother" story comes from Dainius Junevičius (Vilnius photo historian, former ambassador of Lithuania to Poland). Ask him for his source.
- Claude's to-do: search postcards with the imprint "F. Zaniewski Wilno" (Polona, epaveldas, eBay/allegro) and the Wrocław cynkografia 1945–1950s.

### Painting photos (2026-11-17)
- Painting 1 (seen): river capriccio with a ruined tower (spire and pennant) and stairs, red-roofed house, half-timbered gables (X-bracing) on the left, a boat with figures, a distant city with a mountain, and staffage in the foreground.
- Genre: an 18th-c. "Rhine fantasy" / capriccio in the Dutch-Flemish manner (cf. Herman Saftleven, Jan Griffier, the Schütz family of Frankfurt). Half-timbered gables and Rhine scenery are standard motifs of the genre, so they are not proof of a specific place. This fits dr Juszczak's "18th c. provincial".
- Marek: the painting with the boat IS "Połów ryb o poranku". Prof. Paciorek (Kraków ASP; he conserved the St Mary's altarpiece) found NO signature. The only clue is blades of grass forming a large "M" in the lower right corner, which matches the dark mark I saw. Marek only SAW the IR/UV images live (c. 2003) and has no copies, so ask ASP for the documentation (T11). The varnish has yellowed a lot since then.
- Next: photos of the backs, the canvas and the stretchers; the ASP 2003 report; the dimensions.

### Nancy search log (2026-11-17, via Piotr's screenshots)
- R 61 (Saint-Sébastien baptism index): **no Fleury in 1744–1750** (checked F and D/"de Fleury", images 314–318). Found: Anne Fleury, baptised 15 XI 1722, act 2678 (H relative).
- R 39 (Saint-Nicolas), image 150 = the register for June 1767, not the index. Found: Magdeleine Charlotte, daughter of **Jean Joseph Berlin de Fleury**, écuyer, and Barbe Françoise Raulin, born June 1767. Probably a different noble family ("Berlin de Fleury"); noted only.

- R 39 Saint-Nicolas index (chronological répertoire, image 23): Apr–Jul 1745, NO Fleury.
- R 44 Saint-Pierre alphabetical index 1731–1748 (image 24): NO Fleury.
- R 23 Saint-Epvre register (images 24–25, acts 138–152 = 20 IV – 4 VI 1745): NO Fleury; every act read.
- R 85 Saint-Vincent-Saint-Fiacre index 1721–1765 (image 26): NO Fleury.
- R 52 Saint-Roch register (images 210–211 = 13 IV – 28 V 1745): NO Fleury.
- R 2 Notre-Dame register (images 564, 566 = 19 III – 9 V 1745; 565 is an out-of-order sheet, Feb/June 1745): NO Fleury. Image 567 (burials 5–7 V, Conard×Rousselot marriage): NO Fleury. => ALL 7 Nancy parishes negative for Apr–May 1745. Next hypotheses: (a) private baptism (ondoiement) with ceremonies supplied later; (b) year 1746; (c) born in Lunéville or elsewhere in Lorraine; (d) the date 1 V 1745 is unreliable, so first find its SOURCE (Minakowski? Powązki grave?).
- R 1 Notre-Dame: covers only 1595–1688 + index 1765–76, irrelevant. R 2 (1740–1754) would NOT open on 17 XI; retry later.
- Remaining: Notre-Dame R 2; R 108 noble families; then hypotheses: born 1746, or Lunéville.
- (old line) Remaining: Saint-Vincent-Saint-Fiacre (index R 85 / register R 86), Saint-Roch R 52, Notre-Dame R 2, R 108 (noble families). NB: the "1 V 1745 Nancy" date may come from secondary sources or from the 1811 death age (65), so it may be approximate (1745–46) or the place may be wrong (Lunéville?).

### Branch L18 – Louis XVIII in Warsaw (Marek, 2026-11-17)
- FAM/H: Filip looked after the exiled court of Louis XVIII in Warsaw. Louis XVIII paid for hospitality with jewels and objects, which may be the source of the paintings. Louis XVIII (Comte de Lille) did live in Warsaw 1801–1804 (Biały Domek, Łazienki; Kazanowski palace) and was a grandson of Marie Leszczyńska (fact, S88). Filip's role is unverified.
- FAM: Filip's French sabre later hung in Józef Fleury's study in Wilno among a collection of paintings.
- H: ancestors were military men, possibly musketeers at Versailles.
- AGAD request (T12): ennoblement 1790; Gabinet SA papers (Zbiór Popielów) for adjutants; Józef Poniatowski archive (godfather 1799); Louis XVIII's household 1801–04. Also French sources: the papers of Louis XVIII's émigré court (Archives nationales, series on the "cour de Mitau/Varsovie").
- Stanisław–Maria letters (Nancy/Lunéville): 1725–1766, before Filip's time; low priority for the paintings.

### Branch H – exhumation of Feliks (family, 2026-11-17)
- The family confirms the grave was exhumed. That explains the 30 XII 1965 burial date for a man who died 30 VI 1947, so 1965 = reburial at Osobowice 67/1/1.
- An exhumation needs a permit from the sanitary inspectorate (sanepid) and leaves records at the cemetery administration (ZCK), covering where he lay first and who applied (probably Czesława or Tadeusz).
- Ask ZCK Wrocław (biuro@zck.wroc.pl, 71 328 70 20): the exhumation and burial records for Feliks Zaniewski, who else is in 67/1/1, and the grave's status after the lease expired in 1985.

### Branch I – inheritance case files (Marek, 2026-11-17: "po wszystkich członkach rodziny ze strony ojca był przeprowadzony spadek")
- A court order confirming who inherits (postanowienie o stwierdzeniu nabycia spadku) gives exact death dates and places and names the heirs and how they were related. The case file usually also holds civil records (akty stanu cywilnego) and sometimes wills.
- Feliks (d. 30 VI 1947, Wrocław): the case likely went to the Wrocław district court (Sąd Grodzki in 1947). The old files may now be at the State Archives in Wrocław. The order would name Czesława and the children, so it would also show whether Tadeusz had siblings.
- Czesława: same route; her death date is unknown.
- Tadeusz (d. 29 IV 1994, Zakopane): the case went to the district court in Zakopane (Sąd Rejonowy).
- First ask Marek for copies of the court orders he has. They give case numbers (sygnatura), and with a number the court or the archive can find the file.
- Russian notarial documents (Wilno) may be inheritance deeds too. Translate them when the photos arrive.

## WORKING RULES (Piotr, 2026-11-17)
1. Claude checks every angle that can be searched online (Geneteka, FamilySearch indexes, Skanoteka, archive catalogues, web) itself and right away. Piotr should not have to remember to ask.
2. Anything blocked (VPN/geo-block, login, email, phone, photos from Marek) goes into the PIOTR TODO list below AND into graph.json "todo" (shown under "Do zrobienia" in the tree page). Remove an item when it's done.

## PIOTR TODO (blocked for Claude)
- T1 [VPN France] Nancy baptism of Filip, 1 V 1745: archives.meurthe-et-moselle.fr, parishes St-Epvre, St-Sébastien, Notre-Dame, St-Roch, St-Nicolas, St-Pierre
- T2 [FamilySearch login] Wilno 1918 marriage no. 2, Feliks Zaniewski × Czesława Wygonowska (Feliks's parents)
- T3 [FamilySearch login] Wilno 1914 death no. 335, Jerzy Wygonowski, son of Jan
- T4 [Geneanet login] "Fleury" Nancy 1745 transcriptions
- T5 [email from Marek] Muzeum Narodowe w Gdańsku: Fleury items and the Połocka house plan
- T6 [email/phone] ZCK Wrocław: exhumation of Feliks, grave 67/1/1, Czesława
- T11 [email from Marek] ASP Kraków: copy of the 2002–03 conservation documentation (Paciorek): IR/UV, before/after, reverse of the canvas, pigment report
- T7 [photos from Marek] all remaining document photos
