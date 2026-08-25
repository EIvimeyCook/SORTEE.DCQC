<p align="center">
  <img src="https://raw.githubusercontent.com/SORTEE/DCQC/main/inst/DCQC/www/circle_black.png" width="200"/>
</p>

<div align="center">
  <h1>DCQC</h1>
  <p><b>Data and Code Quality Control for ecology and evolutionary biology</b></p>
  <p>
    <img src="https://img.shields.io/badge/lifecycle-experimental-orange.svg" alt="Lifecycle: experimental">
    <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License: MIT">
    <img src="https://img.shields.io/badge/R-%3E%3D%204.1-blue.svg" alt="R >= 4.1">
  </p>
</div>

---

## Overview

`DCQC` is an R package that ships a single Shiny application to help **data editors** carry out structured quality control of the data and code archived alongside a manuscript.

The app operationalises the **SORTEE guidelines for data and code quality control** ([Pick *et al.* 2026](https://doi.org/10.24072/pcjournal.687)) as an interactive, six-stage checklist. Rather than working from a PDF of the guidelines and a blank document, an editor works through the relevant stages in the browser, records a Yes/No verdict and a free-text comment against each item, and exports a formatted report to return to the journal or the authors.

The intent is to make data and code checks **consistent between editors, transparent to authors, and quick enough to actually do** — the three things that most often prevent quality control from happening at all.

## The six stages

The checklist contains **15 items** grouped into six stages. Stages are selected at launch, so an editor reviewing only archived data (or only computational reproducibility) is not shown items that do not apply.

| Stage | Focus | Items |
|:--|:--|:--|
| **1** | Data must be archived and adhere to FAIR guiding principles | 1–5 |
| **2** | Archived data corresponds with the data reported in the manuscript | 6 |
| **3** | Code must be archived and adhere to FAIR guiding principles | 7–11 |
| **4** | Archived code corresponds with the workflow reported in the manuscript | 12 |
| **5** | Archived code runs with the archived data | 13 |
| **6** | Results can be computationally reproduced by running the archived code | 14–15 |

Stages 1 and 3 cover accessibility in an open repository with a persistent DOI, licensing, completeness, interoperable (non-proprietary) file formats, and adequate metadata. Stages 2 and 4 check correspondence between what is archived and what the manuscript claims. Stages 5 and 6 cover execution and computational reproducibility of numeric results and figures, with an option to record the tolerance applied — for example the percentage discrepancy measure of [Hardwicke *et al.* (2021)](https://doi.org/10.1098/rsos.201494).

## Installation

`DCQC` is not on CRAN. Install the development version from GitHub:

```r
# install.packages("devtools")
devtools::install_github("SORTEE/DCQC")
```

### Additional requirements

Export renders an R Markdown template to PDF, which needs **Pandoc** and a **LaTeX** distribution in addition to the declared package dependencies:

```r
install.packages("rmarkdown")

# If you do not already have LaTeX installed:
install.packages("tinytex")
tinytex::install_tinytex()
```

## Usage

The package exports one function:

```r
library(DCQC)
DCQC()
```

This launches the Shiny app. The workflow is:

1. **Set up the review.** A modal collects the paper title, your name as reviewer, and the journal, then asks which stages to review. At least one stage must be selected.
2. **Work through the checklist.** Each item shows the full guideline text, a **Yes / No** toggle, and a comment box. Comments are where you record what was missing, what you fixed, and what the authors need to address — they carry most of the value in the final report.
3. **Export.** *Download Text Report* renders a dated report containing every item you answered, its verdict, and its comment, headed with the manuscript, journal, and reviewer details.

Nothing is transmitted anywhere: the app runs locally and the report is written to your machine.

## Report output

The exported report is generated from `inst/rmd/DCQCreport.Rmd` and contains:

- Manuscript title, journal, reviewer name, and report date
- One section per answered checklist item, with the guideline text, the Yes/No response, and the reviewer's comment (or *"No comment provided."*)

Items belonging to unselected stages, and items left unanswered, are omitted rather than reported as failures.

## Dependencies

`bslib`, `shiny`, `shinyalert`, `shinyjs`, `shinyWidgets`, `tippy` (declared), plus `rmarkdown` and a LaTeX engine at export time.

## Contributing

Bug reports, feature requests, and pull requests are welcome via [GitHub Issues](https://github.com/SORTEE/DCQC/issues). Because the checklist text is a direct implementation of a published, community-agreed standard, changes to the **wording of the items themselves** should be raised as an issue for discussion first — the app should track the guidelines rather than diverge from them.

## Citation

If you use `DCQC` in an editorial workflow or in research, please cite the guidelines it implements:

> Pick, J. L., Allen, B. J., Bachelot, B., Bairos-Novak, K. R., Brand, J. A., Class, B., Dallas, T., D'Amelio, P. B., Fenollosa, E., Fernández-Juricic, E., Gomes, D. G. E., Grainger, M. J., Guillemaud, T., John, C., Krasnow, R., Lagisz, M., Lequime, S., Maynard, D. S., Nakagawa, S., O'Dea, R. E., Paquet, M., Petitjean, Q., Sánchez-Tójar, A., van Dis, N. E., Wilson, L. A. B., & Ivimey-Cook, E. R. (2026). The SORTEE guidelines for data and code quality control in ecology and evolutionary biology. *Peer Community Journal*, **6**, e20. https://doi.org/10.24072/pcjournal.687

and the software:

> Ivimey-Cook, E. R., & Pick, J. L. (2026). *DCQC: Data and code quality control for ecology and evolutionary biology*. R package version 0.0.0.9000. https://github.com/SORTEE/DCQC

## References

- Pick, J. L., *et al.* (2026). The SORTEE guidelines for data and code quality control in ecology and evolutionary biology. *Peer Community Journal*, **6**, e20. https://doi.org/10.24072/pcjournal.687 (preprint: https://doi.org/10.32942/X24P8S)
- Hardwicke, T. E., Bohn, M., MacDonald, K., Hembacher, E., Nuijten, M. B., Peloquin, B. N., deMayo, B. E., Long, B., Yoon, E. J., & Frank, M. C. (2021). Analytic reproducibility in articles receiving open data badges at the journal *Psychological Science*: an observational study. *Royal Society Open Science*, **8**(1), 201494. https://doi.org/10.1098/rsos.201494

## License

MIT © Edward R. Ivimey-Cook and Joel L. Pick. See [LICENSE](LICENSE).

---

<p align="center">
  Developed under the <a href="https://www.sortee.org/">Society for Open, Reliable, and Transparent Ecology and Evolutionary Biology (SORTEE)</a>.
</p>

