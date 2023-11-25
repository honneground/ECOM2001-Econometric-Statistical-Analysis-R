# Financial Asset Returns and Portfolio Analysis

- **Unit**: Quantitative Techniques for Business (`ECOM2001`)
- **Study Period**: 2023 Trimester 3A
- **Degree Programme**: Bachelor of Information Technology — Awarded with Distinction by Curtin University
- **Overall Unit Mark**: 87 (High Distinction)

An R Markdown analysis of Home Depot (`HD`), Intel (`INTC`) and PepsiCo (`PEP`). The source combines data retrieval, figures, statistical tests, written interpretation and the comparison of three two-asset portfolios.

## Assignment context and constraints

The empirical project assigned three stocks and required their adjusted daily prices from 1 January 2000 through the date the analysis was run. The work had to explain its R code, present formatted tables and figures, and connect statistical results to an investor's decisions.

The required analysis covered price and return time series, return distributions and summary statistics, tests of whether mean returns differ from zero and from each other, correlations and their significance, and an investment recommendation. Hypothesis-testing sections needed to state the hypotheses, significance level, test statistic, decision and interpretation, including checks relevant to the chosen test.

## Implemented analysis

The primary deliverable is [`financial_asset_analysis.Rmd`](financial_asset_analysis.Rmd). It contains the executable R chunks and the accompanying analysis:

1. **Data retrieval**: use `tidyquant::tq_get` for the three assigned stocks, retain adjusted prices and organise observations by symbol.
2. **Prices and returns**: plot stock prices, calculate logarithmic returns and visualise their time series and distributions.
3. **Descriptive statistics**: present return summaries and distribution diagnostics in formatted tables and figures.
4. **Mean-return tests**: run two-sided one-sample t tests at a one-percent significance level; compare return variances with Bartlett and Fligner–Killeen tests, then use Welch's one-way ANOVA for the cross-stock mean comparison.
5. **Correlation analysis**: calculate the return correlation matrix and test each stock pair with `cor.test`, with written interpretations of direction and strength.
6. **Portfolio comparison**: use bounded `optim` searches to choose weights for HD/INTC, HD/PEP and INTC/PEP. The objective is expected return minus portfolio variance, including each pair's covariance. Compare the resulting weights and objective values in a table.

The R Markdown source combines code and written discussion with the tables and figures generated when rendering the report.

## Run the analysis

Use R with internet access for stock-price retrieval. RStudio is optional: the document can also be rendered from an R session or terminal. Install the packages used by the source and its rendering workflow:

```r
install.packages(c(
  "tidyquant", "tidyverse", "broom", "knitr", "kableExtra",
  "Hmisc", "lmtest", "rmarkdown", "formatR"
))
```

The document uses `pdf_document` with LaTeX table formatting, so PDF rendering also requires Pandoc and a LaTeX installation. Open the `.Rmd` in RStudio and choose **Knit**, or run from the project directory:

```bash
Rscript -e 'rmarkdown::render("financial_asset_analysis.Rmd")'
```

The data request starts at `2000-01-01` without a fixed end date. Rerunning it retrieves the data available at that time; the source's written numerical discussion records the original analysis.
