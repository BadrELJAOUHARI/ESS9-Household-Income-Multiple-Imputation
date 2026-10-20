# ESS Round 9 data (edition 2.0)

This folder intentionally contains **no survey microdata**. The European Social Survey recommends linking to the official portal instead of hosting ESS datasets on third-party websites.

## Getting the exact file used by this project

1. Find the **ESS Round 9 edition 2.0** Stata file named `ESS9e02.dta` at the [University of Michigan / openICPSR archive](https://www.openicpsr.org/openicpsr/project/134501/version/V1/view?path=%2Fopenicpsr%2F134501%2Ffcr%3Aversions%2FV1%2FFinalDataPackage%2Fdta%2FESS9e02.dta&type=file). The listing identifies a 36.1 MB file. You may be asked to sign in.
2. For the authoritative survey source and documentation, see the [ESS Data Portal](https://ess.sikt.no/en/datafile/b2b0bf39-176b-4eca-8d26-3c05ea83d2cb). Its default current edition may not be the older edition required for exact reproduction.
3. Place the Stata file at `ess/ESS9e02.dta` and run `quarto render report.qmd` from the project root.

The project references edition **2.0** and uses a dataset containing **47,086 respondents across 27 countries**. The original report used `ESS9e02.sav` (SPSS); the portfolio version uses `.dta` (Stata) via `haven::read_dta()`.

## Attribution and use

**Producer:** European Social Survey (ESS ERIC). **Dataset:** ESS Round 9 (2018/2019), edition 2.0. ESS datasets are licensed [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). Follow the applicable conditions and cite the survey in any reuse. The full dataset is intentionally excluded from this GitHub repository, following the [ESS recommendation](https://www.europeansocialsurvey.org/contact/disclaimer).

The openICPSR archive is a third-party replication source, not a substitute for the original ESS attribution. No byte-level comparison with the historical ESS SPSS release has been made.

## File Citation (openICPSR)

Dorn, David, and Zweimüller, Josef. *Data and Code for: Migration and Labor Market Integration in Europe: FinalDataPackage: dta: ESS9e02.dta.* Nashville, TN: American Economic Association [publisher], 2021. Ann Arbor, MI: Inter-university Consortium for Political and Social Research [distributor], 2021-07-12. [https://doi.org/10.3886/E134501V1-218768](https://doi.org/10.3886/E134501V1-218768)

To view the citation for the overall project, see [http://doi.org/10.3886/E134501V1](http://doi.org/10.3886/E134501V1).
