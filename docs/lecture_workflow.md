# Lecture Workflow

Denne siden dokumenterer arbeidsflyten for å bygge forelesninger basert på Jupyter Notebooks.

## Oversikt

Arbeidsflyten består av følgende steg:

1. Utvikle innhold i separate notebooks
2. Merge notebooks til én forelesningsnotebook
3. Tagge celler som ikke skal vises
4. Generere slides
5. Kontrollere resultatet før undervisning

---

## 1. Utvikle innhold

Forelesningsmaterialet utvikles i mindre notebooks organisert etter tema og publisert som jupyter book.

Eksempler:

- Preface
- Introduction
- Core Concepts
- Examples
- Summary

Fordeler:

- Enklere vedlikehold
- Tydelig struktur
- Gjenbruk av innhold mellom forelesninger

---

## 2. Merge notebooks

De enkelte notebookene slås sammen til én forelesningsnotebook.

Typisk brukes `nbmerge` eller tilsvarende verktøy.

Etter merge bør man kontrollere:

- rekkefølge på celler
- slide-inndeling
- metadata
- bilder og output

### Eksempel Merge notebooks

nbmerge 00_preface/*.ipynb 01_introduction/*.ipynb > Lecture0.ipynb

Hvis du får Unicode-feil i Windows:

PYTHONUTF8=1 nbmerge 00_preface/*.ipynb 01_introduction/*.ipynb > Lecture0.ipynb

---

## 3. Tagging av interne celler

Celler som kun brukes under utvikling eller testing merkes med passende tags.

Vanlige eksempler:

- `remove-input`
- `remove-cell`
- andre prosjektspesifikke tags

Eksempler på innhold som kan tagges:

- testceller
- løsningsforslag
- debug-utskrifter
- midlertidige eksperimenter

Kjør tag_cells.py slik at celler med # TEST CELL får taggen remove-input.

3. Verifiser tagger

grep -n 'remove-input' Lecture0.ipynb

Kontroller alltid at taggene faktisk er lagret i notebook-metadata.

---

## 4. Generering av slides

Slides genereres fra den sammenslåtte notebooken.

Ved bruk av `nbconvert` kan tagger brukes til å skjule kode eller fjerne celler fra presentasjonen.

Merk:

- RISE viser notebooken live.
- RISE respekterer normalt ikke automatisk `remove-input`-tagger.
- For reproducerbare presentasjoner anbefales genererte HTML-slides.

### Generer Reveal.js-slides med nbconvert

jupyter nbconvert Lecture0.ipynb --to slides --TagRemovePreprocessor.enabled=True --TagRemovePreprocessor.remove_input_tags=remove-input

### Åpne slidene i nettleser

start Lecture0.slides.html
---

## 5. Kvalitetssikring

Før forelesning bør følgende kontrolleres:

### Faglig innhold

- Alle eksempler fungerer
- Resultater er oppdaterte
- Lenker virker

### Presentasjon

- Slide-inndelingen er naturlig
- Bilder vises korrekt
- Fontstørrelser er lesbare

### Opprydding

- Testceller er skjult
- Midlertidige kommentarer er fjernet
- Unødvendig kode er ryddet bort

---

## Feilsøking

### Kode vises fortsatt i slides

Kontroller at:

- taggene finnes i `metadata.tags`
- korrekt preprocessor er aktivert
- slidene er regenerert etter tagging

### Kode skjules ikke i RISE

Dette skyldes ofte at RISE ikke bruker de samme preprocesseringsmekanismene som nbconvert.

### Unicode-feil ved merge

Problemet skyldes ofte tegnkoding i Windows-terminalen. Kontroller at verktøyene bruker UTF-8.

---

## Vedlikehold

Denne arbeidsflyten bør oppdateres når:

- nye verktøy tas i bruk
- notebook-strukturen endres
- presentasjonsplattformen endres
- automatisering legges til

Målet er at en forelesning skal kunne bygges reproducerbart fra kildefilene med minimal manuell innsats.