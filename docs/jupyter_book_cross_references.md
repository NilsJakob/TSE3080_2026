# Jupyter Book Cross-Referencing docs

## Figures

### Define a figure

````md
```{figure} ../images/magnetic_core.png
---
width: 500px
name: fig-magnetic-core
---
Magnetic core with coil.
```
````

### Refer to a figure by number

```md
Figure {numref}`fig-magnetic-core` shows the magnetic circuit.
```

### Refer to a figure by title

```md
See {ref}`fig-magnetic-core`.
```

---

## Sections

### Define a section label

```md
(sec-magnetic-flux)=

## Magnetic Flux
```

### Reference a section

```md
See {ref}`sec-magnetic-flux`.
```

---

## Chapters / Documents

### Reference another notebook or markdown file

```md
See {doc}`../12_magnetic_circuits/magnetic_fundamentals`.
```

### Custom link text

```md
See {doc}`the magnetic fundamentals chapter <../12_magnetic_circuits/magnetic_fundamentals>`.
```

---

## Equations

### Label an equation

```md
$$
\mathcal{F}=\Phi\mathcal{R}
$$(eq-reluctance)
```

### Reference the equation

```md
Equation {eq}`eq-reluctance` shows the magnetic analogue of Ohm's law.
```

---

## Tables

### Label a table

````md
```{table} Electrical and magnetic circuit analogies
:name: tbl-analogies

| Electrical | Magnetic |
|------------|-----------|
| Voltage | MMF |
| Current | Flux |
| Resistance | Reluctance |
```
````

### Reference a table

```md
Table {numref}`tbl-analogies` summarizes the analogies.
```

---

## Footnotes

### Create a footnote

```md
Ampère's law is fundamental.[^ampere]

[^ampere]: Named after André-Marie Ampère.
```

---

## Internal Links

### Link to a section directly

```md
{ref}`sec-magnetic-flux`
```

### Custom text

```md
[Magnetic Flux Section](#sec-magnetic-flux)
```

---

## Glossary Terms

### Define a term

````md
```{glossary}

Reluctance
  Opposition to magnetic flux.
```
````

### Reference the term

```md
{term}`Reluctance`
```

---

## Recommended Naming Convention

Use unique labels throughout the entire book:

```text
fig-magnetic-core
fig-transformer-model
fig-threephase-system

sec-magnetic-flux
sec-ampere-law

eq-reluctance
eq-ampere-law

tbl-analogies
tbl-machine-data
```
