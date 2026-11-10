# Financial Asset Returns and Portfolio Analysis

- **Unit**: Quantitative Techniques for Business (`ECOM2001`)
- **Study Period**: 2023 Trimester 3A
- **Degree Programme**: Bachelor of Information Technology — Awarded with Distinction by Curtin University
- **Overall Unit Mark**: 87 (High Distinction)

An R Markdown analysis of Home Depot (`HD`), Intel (`INTC`) and PepsiCo (`PEP`). The source combines data retrieval, figures, statistical tests, written interpretation and the comparison of three two-asset portfolios.

<table>
  <thead>
    <tr>
      <th colspan="6">Curtin University &bull; Bachelor of Information Technology</th>
    </tr>
  </thead>
  <tbody>
    <tr align="center" style="font-weight: bold; background-color: #f6f8fa;">
      <td>2022 T3A</td>
      <td>2023 T1A</td>
      <td>2023 T2A</td>
      <td>2023 T3A</td>
      <td>2024 T1A</td>
      <td>2024 T2A</td>
    </tr>
    <tr>
      <td valign="top">
        <abbr title="Fundamentals of Programming (92 HD)"><b>COMP1005</b></abbr><br>
        &bull; <a href="https://github.com/honneground/COMP1005-Vampire-Ecosystem-Simulation">Vampire Eco</a><br>        &bull; <a href="https://github.com/honneground/COMP1005-Vehicle-Emissions-Analyzer">Emissions</a><br>      </td>
      <td valign="top">
        <abbr title="Data Structures and Algorithms (89 HD)"><b>COMP1002</b></abbr><br>
        &bull; <a href="https://github.com/honneground/COMP1002-StudyHelp-Academic-Network">StudyHelp</a><br>        &bull; <a href="https://github.com/honneground/COMP1002-Advanced-Data-Structures-and-Visualizer">Visualizer</a><br>        <abbr title="Unix and C Programming (90 HD)"><b>COMP1000</b></abbr><br>
        &bull; <a href="https://github.com/honneground/COMP1000-Terminal-Maze-Survival-Game">Maze Survival</a><br>        &bull; <a href="https://github.com/honneground/COMP1000-Terminal-Maze-Darkness-Game">Maze Darkness</a><br>        &bull; <a href="https://github.com/honneground/COMP1000-Bookstore-Transaction-Simulator">Bookstore</a><br>        <abbr title="Introduction to Software Engineering (95 HD)"><b>ISAD1000</b></abbr><br>
        &bull; <a href="https://github.com/honneground/ISAD1000-Software-Testing-and-Pocket-Beast-Game">Pocket Beast</a><br>      </td>
      <td valign="top">
        <abbr title="Unix Systems Programming (88 HD)"><b>COMP2002</b></abbr><br>
        &bull; <a href="https://github.com/honneground/COMP2002-Parallel-Directory-File-Calculator">Dir Calculator</a><br>        <abbr title="Operating Systems (80 HD)"><b>COMP2006</b></abbr><br>
        &bull; <a href="https://github.com/honneground/COMP2006-Customer-Queue-Concurrency-Simulation">Queue Sim</a><br>      </td>
      <td valign="top" style="background-color: #f1f8ff; border: 2px solid #0969da;">
        <abbr title="Database Systems (80 HD)"><b>ISYS2014</b></abbr><br>
        &bull; <a href="https://github.com/honneground/ISYS2014-Relational-Database-Management-System">FootyStats DB</a><br>        <abbr title="Quantitative Techniques for Business (87 HD)"><b>ECOM2001</b></abbr><br>
        &bull; <b>&#128073; Econometric R</b><br>      </td>
      <td valign="top">
        <abbr title="Financial Decision Making (93 HD)"><b>ACCT1002</b></abbr><br>
        &bull; <a href="https://github.com/honneground/ACCT1002-Financial-Decision-Calculators">Finance Tools</a><br>        <abbr title="Human Computer Interface (71 D)"><b>ICTE3002</b></abbr><br>
        &bull; <a href="https://github.com/honneground/ICTE3002-Lumen-Interaction-Design">Lumen UI</a><br>        <abbr title="Engineering Management and Professional Practice (79 D)"><b>MGMT3000</b></abbr><br>
        &bull; <a href="https://github.com/honneground/MGMT3000-Phone-Router-Repurposing-Design">Phone Router</a><br>      </td>
      <td valign="top">
        <abbr title="Capstone Computing Project 1 (94 HD)"><b>ISAD3000</b></abbr><br>
        &bull; <a href="https://github.com/honneground/ISAD3000-CurtinSG-App-Design">CurtinSG UI</a><br>        <abbr title="Capstone Computing Project 2 (95 HD)"><b>ISAD3001</b></abbr><br>
        &bull; <a href="https://github.com/honneground/ISAD3001-CurtinSG-Student-App">CurtinSG App</a><br>        <abbr title="Advanced Computer Communications (88 HD)"><b>CNCO3002</b></abbr><br>
        &bull; <a href="https://github.com/honneground/CNCO3002-Multi-Service-Socket-Server">Socket Server</a><br>      </td>
    </tr>
  </tbody>
</table>


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

---

## Portfolio note

This Git repository was created retrospectively from the original project code, with assistance from OpenAI Codex and Antigravity in curating the repository and writing this README for publication. The initial commit timestamp is backdated to the original coursework submission date, followed by the final release commit.


