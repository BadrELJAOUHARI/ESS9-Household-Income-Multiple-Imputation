# Missing Income in Europe: Survey-Weighted Multiple Imputation

### A five-country study using European Social Survey Round 9

![R](https://img.shields.io/badge/R-Statistical_Analysis-276DC3?logo=r&logoColor=white) ![MICE](https://img.shields.io/badge/MICE-Multiple_Imputation-7356A6) ![ESS](https://img.shields.io/badge/Data-ESS_Round_9-237A57) ![Quarto](https://img.shields.io/badge/Quarto-Reproducible_Report-39729E?logo=quarto&logoColor=white)

**What happens when people decline to disclose their household income in a survey?** And does accounting for sampling weights during imputation improve the resulting data?

This project studies item nonresponse in the *European Social Survey (ESS), Round 9 (2018–2019)*. We investigate household net-income deciles (`hinctnta`) across **Italy, Spain, Finland, Sweden, and the Netherlands**, comparing different strategies for imputing missing values while recognizing differences between national contexts.

The work was completed as a **group assignment in Survey Data Analysis** (January 2026). It includes theoretical background, code and a full analysis in [Quarto](report.qmd).

## Research design

| Dimension | What we compare |
|:--|:--|
| Imputation strategy | Single imputation versus multiple imputation by chained equations (**MICE**) |
| Survey weighting | Imputation with and without sampling weights; weights retained for the final survey analysis |
| Geographic scope | Pooled five-country, North/South regional, and country-specific predictor specifications |
| Weighted algorithm | Weighted predictive mean matching, using `miceadds` |
| Evaluation | Within-person imputation variability, income-decile distributional deviation, and chi-square comparisons |

The North group includes **Finland, the Netherlands and Sweden**; the South group includes **Italy and Spain**. The comparison draws on welfare-regime perspectives discussed in the report, while recognizing that these groupings simplify the diversity within and between countries.

## Data at a glance

The uploaded ESS9 edition 2.0 Stata file has **47,086 rows across 27 countries**. The project analyzes five selected countries. Their baseline missing-income rates, verified against the supplied file, are:

| Country | Respondents | Missing `hinctnta` |
|:--|--:|--:|
| Italy | 2,745 | 44.4% |
| Spain | 1,668 | 27.8% |
| Netherlands | 1,673 | 16.9% |
| Finland | 1,755 | 6.9% |
| Sweden | 1,539 | 6.6% |

These different rates make a single imputation approach across all countries a question worth investigating.

## Selected findings from the original report

- **No strategy dominates across all criteria.** The choice depends on whether the goal is within-person consistency, proximity to a uniform-decile benchmark, or fidelity to the observed income distribution.
- **Unweighted multiple imputation** with region-specific predictors yielded particularly low within-person variation in this project's evaluations. This *descriptive stability measure* is not, by itself, evidence of valid statistical uncertainty quantification.
- **Single imputation** often produced income distributions closer to the comparison benchmarks used in the report.
- **Adding survey weights during imputation** produced mixed effects that depended on the geographical predictor specification.

**Important methodological limitation:** The report collapses imputed income deciles using a mode-based rule for descriptive comparison. This is **not equivalent to pooling inferential estimates using Rubin's rules**; the resulting single completed data set should not be treated as preserving full multiple-imputation uncertainty. The uniform income-decile distribution is an evaluative benchmark, not a guaranteed true distribution in a finite survey sample.

Read the full [Quarto analysis](report.qmd) for explanations, model specifications, comparisons and references. The original report is preserved apart from the small import-path change described below.

## Reproduce the analysis

**Prerequisites:** R **4.4.3 or later** (recommended in the report), [Quarto](https://quarto.org/docs/get-started/), and the following R packages:

```r
install.packages(c(
  "tidyverse", "haven", "survey", "mice", "miceadds",
  "future", "furrr", "knitr"
))
```

**1. Get the data.** Download the exact **ESS Round 9 edition 2.0** file `ESS9e02.dta`. See [ess/README.md](ess/README.md) for data sources and attribution. Save it as `ess/ESS9e02.dta`.

**2. Run the report** from the repository root:

```bash
quarto render report.qmd
```

The Quarto document is configured to render **HTML** and contains the analysis, tables, visualizations, and generated evaluation exports. Depending on your computer, the multiple imputation models may take considerable time and use several CPU cores. The report does not pin exact package versions, and full end-to-end reproduction has **not yet been tested** in this repository.

**Source compatibility note:** The original class assignment read the SPSS file using `haven::read_sav("./ess/ESS9e02.sav")`. This portfolio version changes that **one data-loading line** to `haven::read_dta("./ess/ESS9e02.dta")` to match the supplied edition 2.0 Stata file. Statistical code and narrative are otherwise unchanged.

## Project files

```text
ess-income-nonresponse-imputation/
├── README.md          # Project overview, key methods and findings
├── report.qmd         # Original co-authored analysis and R code
├── ess/
│   └── README.md      # Where to download the data (no dataset included)
└── .gitignore         # Avoid committing third-party data and generated files
```

## Data source, licensing and attribution

European Social Survey, **ESS Round 9 (2018)**, **edition 2.0**. The ESS data are licensed under **CC BY-NC-SA 4.0**. The ESS recommends that datasets be linked from the [ESS Data Portal](https://ess.sikt.no/en/datafile/b2b0bf39-176b-4eca-8d26-3c05ea83d2cb) rather than mirrored on external websites, so the original data file is **not included** here. For the specific older file, see the [openICPSR listing](https://www.openicpsr.org/openicpsr/project/134501/version/V1/view?path=%2Fopenicpsr%2F134501%2Ffcr%3Aversions%2FV1%2FFinalDataPackage%2Fdta%2FESS9e02.dta&type=file). The latest ESS edition may differ from the edition used in the analysis.

This README describes the co-authored student analysis and does not imply endorsement by ESS ERIC or the institutions distributing its data.

## Authors

This is a **collaborative academic project**, with all four original contributors credited as in the Quarto report:

- Klaas Dieleman
- Badr El Jaouhari
- Fay de Lange
- Ludo Mels

*Survey Data Analysis coursework — 14 January 2026.*
