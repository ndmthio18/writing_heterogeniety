# Hetero_MRI_Modelling_WRR — manuscript working folder

Version-controlled working copy of the Water Resources Research manuscript on
evaporation-driven solute redistribution in a heterogeneous F36/W3 sand packing
imaged with ²³Na/¹H MRI and analysed with DuMuˣ simulations.

The Word draft (`Hetero_MRI_Modelling_WRR_draft1.docx`) is kept here unchanged as
the content reference. The LaTeX project in `latex/` reproduces that draft in the
AGU/Water Resources Research layout.

## Contents

| Path | Description |
|---|---|
| `Hetero_MRI_Modelling_WRR_draft1.docx` | Word draft 1, source of the text and figures |
| `latex/main.tex` | AGU manuscript (title page, body, tables, figures, bibliography) |
| `latex/literature.bib` | 25 references transcribed from the draft reference list |
| `latex/agujournal2019.cls` | AGU journal class (copied from `20DPNM/review-R2`) |
| `latex/pictures/` | Figure artwork extracted from the Word draft |
| `latex/main.pdf` | Rendered manuscript (tracked, so co-authors can read it without a TeX installation) |
| `Chapter4_…_Research_Notes.md`, `idea.md`, `WRR_异质土柱…md` | Earlier notes kept for provenance |

## Build

```powershell
cd latex
latexmk -pdf main.tex      # pdflatex + bibtex (apacite), ~20 pages
latexmk -c                 # remove auxiliary files, keep main.pdf
```

The build was verified with TeX Live 2025 (`pdflatex`, `bibtex`, `latexmk`).
Everything is self-contained in `latex/`, so the folder can also be uploaded to
Overleaf as-is.

| Result | Value |
|---|---|
| Pages | 19 |
| Undefined references / citations | none |
| Bibliography entries | 25 |

## Conversion notes (docx → LaTeX)

* Section numbers are generated automatically. The Word draft skipped a 2.5 and
  used "3.4" twice; the LaTeX draft numbers the existing sections 2.1–2.6 and
  3.1–3.8 without reordering or deleting text.
* "Figure X" placeholders in the draft were replaced by numbered `\ref`s; figures
  are numbered in order of first citation (Fig. 1–8).
* "Table 4.1" in the calibration paragraph refers to the imaging-protocol table,
  which is Table 2 here.
* The two Word equations (evaporation rate, Na concentration calibration) were
  reconstructed from the embedded Office Math objects.
* Obvious typos were corrected (`Shimojimaa` → Shimojima, `ddensity` →
  density, `Bo field` → *B*₀ field).
* The italic editorial instructions in the draft ("The following text in italic
  can be removed…", "Bridging paragraph to numerical simulations", "Mention
  results of numerical simulations") are rendered as red author notes
  (`\authornote{…}`) so that they stay visible until resolved. Remove all of them
  before submission.
* The key points were written from the abstract because the draft only contained
  three dashes; the authors must confirm them.
* The AGU front/back matter (key points, acknowledgments, open research, conflict
  of interest) is present as placeholders.

## Open items

Sections that have only a heading and a red note in the draft:

* 2.3 Numerical model and boundary conditions
* 2.4 Quantities used for model comparison
* 2.5 Process comparisons and numerical verification
* 2.6 Dimensionless parameters and regime classification
* 3.5 Numerical simulation of the observed redistribution
* 3.6 Regime map of convective redistribution and interdomain coupling
* 3.7 Joint implications for salt accumulation and limits of interpretation
* 4 Conclusions — the numerical-results sentence is still missing
* Acknowledgments, Open Research, Conflict of Interest

Figures still missing artwork (framed placeholders in the PDF):

* Fig. 2 — cumulative water loss and evaporation rate of the experiment
* Fig. 3 — ²³Na-MRI calibration for F36 and W3
* Fig. 7 — recovered Na mass and depth profiles (a–d)
* Fig. 8 — six-panel conceptual model

Artwork available in `pictures/`: Fig. 1 (sample holder and packed sample),
Fig. 4 (first 8 h of ²³Na-MRI), Fig. 5 (full 174 h), Fig. 6 (¹H top slices).

## Version control

This folder is its own Git repository (the surrounding project folder is not a
Git repository, so no parent-level ignore rule is required). LaTeX build
artifacts are ignored; `main.pdf` is tracked as the readable snapshot.
