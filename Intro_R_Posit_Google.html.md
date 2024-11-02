---
title: "Introduction to Posit, R and RStudio IDE"
subtitle: "Workshop Guide"
author: 
  - Kamarul Imran Musa
  - Jason Ng
date: last-modified
format:
  html:
    toc: true
    toc-location: left
    code-fold: false
    theme: 
      light: cosmo
      dark: [cosmo, theme-dark.scss]
  pdf:
    toc: true
    number-sections: true
    colorlinks: true
self-contained: true
editor_options: 
  markdown: 
    wrap: 72
execute:
  message: false
  warning: false
  keep-md: true
---





\newpage

# Introduction to Posit Cloud, R and RStudio IDE

## Posit Cloud

Posit Cloud lets you access Posit’s powerful [set of data science
tools](https://posit.co/products/cloud/cloud/) right in your browser–no
installation or complex configuration required.

### Register for free Posit Cloud account and access our course

Steps:

-   Click POSIT Cloud folder for our workshop at this
    [link](https://posit.cloud/spaces/571287/join?access_code=oTpeMSBq9BqTHaGGZTqTTnGwAm8Fmu7jxcv7Doj9)
-   Proceed with registration if required

![Free registration](posit.png){width="60%"}

### Join the space

![Join the space](space.png){width="70%"}

-   Go to Members area

![Your workspace](images/ts.png)

-   Create new **RStudio project**

![Create a new RStudio project](rstudioproject.png){width="70%"}

-   RStudio interface

![RStudio interface](images/ts_project.png)

## R Programming Language

There are some terms we have to be familiar:

-   packages
-   codes
-   parameters
-   argument

### R packages

R codes are contained with a package. CRAN provides the list of all R
packages.

-   It is accessible at [CRAN
    webpage](https://cran.r-project.org/web/packages/available_packages_by_name.html)
-   There at (of 10 July 2023) almost 20000 R packages listed on [CRAN
    packages webpage](https://cran.r-project.org/web/packages/)
-   Look at [CRAN TaskViews](https://cran.r-project.org/web/views/) if
    you want to know R packages that are grouped based on certain topics
    such as Bayesian, Causal Inference, Epidemiology and many others.
-   There are also many more packages that are not listed on CRAN but
    hosted on other repositories such as GitHub.

If you need to use certain R packages, you have to install it first.
There are two ways of installing R packages into your R IDE:

-   Writing codes in R Console: Type
    `install.packages("nlme", dependencies = TRUE)`, then click ENTER

![Install R package](installpackage2.png){width="70%"}

-   Using GUI in the `Package` pane

![Install R package](installpackage.png){width="70%"}

-   install these packages

    -   `fpp3`

    -   `tidyverse`

![Install required packages](images/install.png)

### R functions

We have to write R scripts to perform desired task in R. R scripts
consists a set of R codes. Users write R scrips in the Console pane or
in R Script file or other R editor such as Quarto or R Markdown
document.

Some simple codes as examples:

`ChickWeight[1:20,]`

`lm(weight ~ Time, data = ChickWeight)`




::: {.cell}

```{.r .cell-code}
ChickWeight[1:20,]
```

::: {.cell-output .cell-output-stdout}

```
   weight Time Chick Diet
1      42    0     1    1
2      51    2     1    1
3      59    4     1    1
4      64    6     1    1
5      76    8     1    1
6      93   10     1    1
7     106   12     1    1
8     125   14     1    1
9     149   16     1    1
10    171   18     1    1
11    199   20     1    1
12    205   21     1    1
13     40    0     2    1
14     49    2     2    1
15     58    4     2    1
16     72    6     2    1
17     84    8     2    1
18    103   10     2    1
19    122   12     2    1
20    138   14     2    1
```


:::

```{.r .cell-code}
lm(weight ~ Time, data = ChickWeight)
```

::: {.cell-output .cell-output-stdout}

```

Call:
lm(formula = weight ~ Time, data = ChickWeight)

Coefficients:
(Intercept)         Time  
     27.467        8.803  
```


:::
:::




### Arguments in R functions

Now, let's type a question mark in front of a function.

For example, type a question mark infront of `lm`. Then click ENTER.




::: {.cell}

```{.r .cell-code}
?lm
```
:::




A window will appear. It will describe the detailed information about
the function. You can see the default paramaters for such function, such
as:

`lm(formula, data, subset, weights, na.action,    method = "qr", model = TRUE, x = FALSE, y = FALSE, qr = TRUE,    singular.ok = TRUE, contrasts = NULL, offset, ...)`

You will see arguments for each parameters:

-   formula
-   data
-   subsets
-   weight

and others

## RStudio IDE

RStudio is an integrated development environment (IDE) for R and Python.
It includes a console, syntax-highlighting editor that supports direct
code execution, and tools for plotting, history, debugging, and
workspace management. RStudio is available in open source and commercial
editions and runs on the desktop (Windows, Mac, and Linux).

There are a few ways to use RStudio:

-   Install it on your computer
-   Use it on the Cloud (POSIT, Amazon, Microsoft, Saturn Cloud)
-   Install and use it on a server (RStudio Workbench)

### Hands on with RStudio IDE

-   Prepare the R environment

Steps:

-   Create a new RStudio project
-   Load required R libraries




::: {.cell}

```{.r .cell-code}
library(tidyverse) #data wrangling and data visualization
library(haven) #read statistical data
library(broom) #tidier results
library(gtsummary) #to perform EDA
library(fpp3) #for time series and forecasting
```
:::




If you received error `there is no package called XXXXXX` then install
the package first then run the `library` function again

![Error when package not yet
installed](images/nopackage.png){width="501"}

-   Read data

First, we read data that we want to analyze into R. In this example, we
will read a file named `imm23.dta` that sits in a folder named
`datasets`.

R then will convert the data into an object named as `imm`. You are free
to write any name to represent the data.




::: {.cell}

```{.r .cell-code}
dataset <- read_csv('health_dataset.csv')
```
:::




You may check the columns and rows of the datasets:

-   columns are variables
-   rows are observations




::: {.cell}

```{.r .cell-code}
glimpse(dataset)
```

::: {.cell-output .cell-output-stdout}

```
Rows: 1,000
Columns: 12
$ hba1c       <dbl> 8.346606, 8.711193, 8.745453, 8.971826, 9.852680, 12.52782…
$ fbs         <dbl> 5.910906, 6.670592, 10.785029, 7.362169, 7.497362, 11.1446…
$ sex         <chr> "male", "male", "male", "female", "female", "male", "male"…
$ age         <dbl> 36.79013, 41.92743, 35.97902, 51.27069, 56.20355, 66.27214…
$ sbp         <dbl> 102.87252, 116.03028, 102.60260, 104.39317, 118.13104, 105…
$ dbp         <dbl> 85.05267, 65.43385, 62.18899, 73.11391, 77.92691, 74.12425…
$ weight      <dbl> 77.42964, 58.26995, 83.36551, 54.74778, 76.34981, 82.72246…
$ whr         <dbl> 0.12138468, 0.15365110, 0.04139635, 1.22958802, 0.19269123…
$ chol        <dbl> 5.259782, 4.243214, 6.836742, 6.531657, 3.523359, 6.291934…
$ tg          <dbl> 5.2650048, 6.1474392, 3.6183344, -0.5153024, 2.5157862, 2.…
$ obese       <chr> "no", "yes", "no", "yes", "yes", "yes", "no", "yes", "no",…
$ historyofdm <chr> "no", "no", "no", "no", "no", "yes", "no", "yes", "no", "n…
```


:::
:::




-   Explore data

You must always explore your data. Examine each variable and each
observation.




::: {.cell}

```{.r .cell-code}
dataset |> 
  tbl_summary(by = sex)
```

::: {.cell-output-display}


```{=html}
<div id="ewykztqafd" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#ewykztqafd table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#ewykztqafd thead, #ewykztqafd tbody, #ewykztqafd tfoot, #ewykztqafd tr, #ewykztqafd td, #ewykztqafd th {
  border-style: none;
}

#ewykztqafd p {
  margin: 0;
  padding: 0;
}

#ewykztqafd .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ewykztqafd .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#ewykztqafd .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ewykztqafd .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ewykztqafd .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ewykztqafd .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ewykztqafd .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ewykztqafd .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ewykztqafd .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ewykztqafd .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ewykztqafd .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ewykztqafd .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ewykztqafd .gt_spanner_row {
  border-bottom-style: hidden;
}

#ewykztqafd .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#ewykztqafd .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ewykztqafd .gt_from_md > :first-child {
  margin-top: 0;
}

#ewykztqafd .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ewykztqafd .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ewykztqafd .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#ewykztqafd .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#ewykztqafd .gt_row_group_first td {
  border-top-width: 2px;
}

#ewykztqafd .gt_row_group_first th {
  border-top-width: 2px;
}

#ewykztqafd .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ewykztqafd .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#ewykztqafd .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#ewykztqafd .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ewykztqafd .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ewykztqafd .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ewykztqafd .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#ewykztqafd .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ewykztqafd .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ewykztqafd .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ewykztqafd .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#ewykztqafd .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ewykztqafd .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#ewykztqafd .gt_left {
  text-align: left;
}

#ewykztqafd .gt_center {
  text-align: center;
}

#ewykztqafd .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ewykztqafd .gt_font_normal {
  font-weight: normal;
}

#ewykztqafd .gt_font_bold {
  font-weight: bold;
}

#ewykztqafd .gt_font_italic {
  font-style: italic;
}

#ewykztqafd .gt_super {
  font-size: 65%;
}

#ewykztqafd .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#ewykztqafd .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#ewykztqafd .gt_indent_1 {
  text-indent: 5px;
}

#ewykztqafd .gt_indent_2 {
  text-indent: 10px;
}

#ewykztqafd .gt_indent_3 {
  text-indent: 15px;
}

#ewykztqafd .gt_indent_4 {
  text-indent: 20px;
}

#ewykztqafd .gt_indent_5 {
  text-indent: 25px;
}

#ewykztqafd .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}

#ewykztqafd div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="&lt;div data-qmd-base64=&quot;KipDaGFyYWN0ZXJpc3RpYyoq&quot;&gt;&lt;div class='gt_from_md'&gt;&lt;p&gt;&lt;strong&gt;Characteristic&lt;/strong&gt;&lt;/p&gt;&#10;&lt;/div&gt;&lt;/div&gt;"><div data-qmd-base64="KipDaGFyYWN0ZXJpc3RpYyoq"><div class='gt_from_md'><p><strong>Characteristic</strong></p>
</div></div></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="&lt;div data-qmd-base64=&quot;KipmZW1hbGUqKiAgCk4gPSA0ODQ=&quot;&gt;&lt;div class='gt_from_md'&gt;&lt;p&gt;&lt;strong&gt;female&lt;/strong&gt;&lt;br /&gt;&#10;N = 484&lt;/p&gt;&#10;&lt;/div&gt;&lt;/div&gt;&lt;span class=&quot;gt_footnote_marks&quot; style=&quot;white-space:nowrap;font-style:italic;font-weight:normal;line-height: 0;&quot;&gt;&lt;sup&gt;1&lt;/sup&gt;&lt;/span&gt;"><div data-qmd-base64="KipmZW1hbGUqKiAgCk4gPSA0ODQ="><div class='gt_from_md'><p><strong>female</strong><br />
N = 484</p>
</div></div><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;line-height: 0;"><sup>1</sup></span></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="&lt;div data-qmd-base64=&quot;KiptYWxlKiogIApOID0gNTE2&quot;&gt;&lt;div class='gt_from_md'&gt;&lt;p&gt;&lt;strong&gt;male&lt;/strong&gt;&lt;br /&gt;&#10;N = 516&lt;/p&gt;&#10;&lt;/div&gt;&lt;/div&gt;&lt;span class=&quot;gt_footnote_marks&quot; style=&quot;white-space:nowrap;font-style:italic;font-weight:normal;line-height: 0;&quot;&gt;&lt;sup&gt;1&lt;/sup&gt;&lt;/span&gt;"><div data-qmd-base64="KiptYWxlKiogIApOID0gNTE2"><div class='gt_from_md'><p><strong>male</strong><br />
N = 516</p>
</div></div><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;line-height: 0;"><sup>1</sup></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">hba1c</td>
<td headers="stat_1" class="gt_row gt_center">9.54 (8.74, 10.38)</td>
<td headers="stat_2" class="gt_row gt_center">9.45 (8.59, 10.37)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">fbs</td>
<td headers="stat_1" class="gt_row gt_center">7.29 (5.83, 8.83)</td>
<td headers="stat_2" class="gt_row gt_center">7.17 (5.71, 8.57)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">age</td>
<td headers="stat_1" class="gt_row gt_center">45 (39, 52)</td>
<td headers="stat_2" class="gt_row gt_center">45 (38, 52)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">sbp</td>
<td headers="stat_1" class="gt_row gt_center">110 (103, 117)</td>
<td headers="stat_2" class="gt_row gt_center">109 (103, 116)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">dbp</td>
<td headers="stat_1" class="gt_row gt_center">75 (70, 79)</td>
<td headers="stat_2" class="gt_row gt_center">75 (70, 80)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">weight</td>
<td headers="stat_1" class="gt_row gt_center">67 (59, 75)</td>
<td headers="stat_2" class="gt_row gt_center">67 (59, 75)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">whr</td>
<td headers="stat_1" class="gt_row gt_center">0.77 (0.42, 1.16)</td>
<td headers="stat_2" class="gt_row gt_center">0.84 (0.49, 1.20)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">chol</td>
<td headers="stat_1" class="gt_row gt_center">4.43 (3.65, 5.33)</td>
<td headers="stat_2" class="gt_row gt_center">4.50 (3.65, 5.46)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">tg</td>
<td headers="stat_1" class="gt_row gt_center">4.62 (3.30, 5.94)</td>
<td headers="stat_2" class="gt_row gt_center">4.60 (3.17, 5.98)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">obese</td>
<td headers="stat_1" class="gt_row gt_center">239 (49%)</td>
<td headers="stat_2" class="gt_row gt_center">267 (52%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">historyofdm</td>
<td headers="stat_1" class="gt_row gt_center">234 (48%)</td>
<td headers="stat_2" class="gt_row gt_center">262 (51%)</td></tr>
  </tbody>
  
  <tfoot class="gt_footnotes">
    <tr>
      <td class="gt_footnote" colspan="3"><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;line-height: 0;"><sup>1</sup></span> <div data-qmd-base64="TWVkaWFuIChRMSwgUTMpOyBuICglKQ=="><div class='gt_from_md'><p>Median (Q1, Q3); n (%)</p>
</div></div></td>
    </tr>
  </tfoot>
</table>
</div>
```


:::
:::




## Example: Revision on linear regression

- Estimation from linear regression in R

Let's show you how to run a linear regression model. From the analysis,
we will be able to estimate the regression parameters.

-   Constant only model

In the constant only model, we choose only the dependent variable. And
we only have one dependent variable `match`.




::: {.cell}

```{.r .cell-code}
mod0 <- lm(hba1c ~ 1, data = dataset)
summary(mod0)
```

::: {.cell-output .cell-output-stdout}

```

Call:
lm(formula = hba1c ~ 1, data = dataset)

Residuals:
    Min      1Q  Median      3Q     Max 
-4.3492 -0.8376  0.0059  0.8815  4.1506 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  9.49864    0.04187   226.8   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 1.324 on 999 degrees of freedom
```


:::
:::




### Univariable model

In univariable model, we specify

-   one dependent variable
-   one covariate or independent variable




::: {.cell}

```{.r .cell-code}
mod1 <- lm(hba1c ~ fbs, data = dataset)
summary(mod1)
```

::: {.cell-output .cell-output-stdout}

```

Call:
lm(formula = hba1c ~ fbs, data = dataset)

Residuals:
    Min      1Q  Median      3Q     Max 
-4.3801 -0.7773 -0.0080  0.8146  3.8961 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  8.03422    0.13070   61.47   <2e-16 ***
fbs          0.20235    0.01722   11.75   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 1.242 on 998 degrees of freedom
Multiple R-squared:  0.1215,	Adjusted R-squared:  0.1206 
F-statistic:   138 on 1 and 998 DF,  p-value: < 2.2e-16
```


:::
:::




### Multivariable model

Now, we let's estimate a multivariable model. A multivaribale model has
one dependent variable and more than one independent variables. For
example:

-   One dependent variable: math
-   Two covariates: fbs, bmi




::: {.cell}

```{.r .cell-code}
mod2 <- lm(hba1c ~ fbs + obese, data = dataset)
summary(mod2)
```

::: {.cell-output .cell-output-stdout}

```

Call:
lm(formula = hba1c ~ fbs + obese, data = dataset)

Residuals:
    Min      1Q  Median      3Q     Max 
-4.2965 -0.7541 -0.0249  0.8425  3.9800 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  7.96066    0.13521  58.877   <2e-16 ***
fbs          0.20113    0.01721  11.689   <2e-16 ***
obeseyes     0.16282    0.07846   2.075   0.0382 *  
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 1.24 on 997 degrees of freedom
Multiple R-squared:  0.1253,	Adjusted R-squared:  0.1235 
F-statistic: 71.38 on 2 and 997 DF,  p-value: < 2.2e-16
```


:::
:::




## Quick tutorial for fpp3 package 

- For more info read 
  - the [fpp3 documentation](https://pkg.robjhyndman.com/fpp3/) 
  - the online Forecasting Principle and Practice [book](https://otexts.com/fpp3/) 

- load library




::: {.cell}

```{.r .cell-code}
library(fpp3)
```
:::




- read a built in data named `aus_retail`




::: {.cell}

```{.r .cell-code}
aus_retail |>
  slice_head(n=4) |>
  View()
```
:::




There are 5 variables. 

  - Time variable is `Month`
  - Outcome variable is `Turnover`

- Make a time series plot for `Series ID`A3349640L




::: {.cell}

```{.r .cell-code}
aus_retail |>
  filter(`Series ID`=="A3349640L") |>
  autoplot(Turnover)
```

::: {.cell-output-display}
![](Intro_R_Posit_Google_files/figure-html/unnamed-chunk-12-1.png){width=672}
:::
:::




- Make a forecast

  - for `Series ID` A3349640L
  - using ETS model
  - for 2 years ahead




::: {.cell}

```{.r .cell-code}
aus_retail |>
  filter(`Series ID`=="A3349640L") |>
  model(ETS(Turnover)) |>
  forecast(h = "2 years")
```

::: {.cell-output .cell-output-stdout}

```
# A fable: 24 x 6 [1M]
# Key:     State, Industry, .model [1]
   State    Industry                                 .model           Month
   <chr>    <chr>                                    <chr>            <mth>
 1 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Jan
 2 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Feb
 3 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Mar
 4 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Apr
 5 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 May
 6 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Jun
 7 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Jul
 8 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Aug
 9 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Sep
10 Victoria Cafes, restaurants and catering services ETS(Turnover) 2019 Oct
# ℹ 14 more rows
# ℹ 2 more variables: Turnover <dist>, .mean <dbl>
```


:::
:::





## Reflection

-   Could you access our course?
-   What do you think would be your main challenges in running R and
    RStudio?
-   Are you interested to run R on your machine?
-   How would you get help if stuck with analysis?
-   Have you tried generative AI such as chatGPT?
-   What is an R package?
-   What is an R code?
-   What is a function?
-   What contains in a function?
