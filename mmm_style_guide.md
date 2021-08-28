MMM R Style Guide
================
Mark Lai
4/9/2020, last updated on 4/16/2020

-   [R Code Style](#r-code-style)
    -   [Naming](#naming)
    -   [Random number generator](#random-number-generator)
    -   [Tools that you can use](#tools-that-you-can-use)
    -   [Functions](#functions)
    -   [Commenting](#commenting)
    -   [Track Changes](#track-changes)
    -   [Git](#git)
    -   [Code Review](#code-review)
-   [Writing manuscripts](#writing-manuscripts)
    -   [Reproducibility](#reproducibility)
    -   [Citation tools](#citation-tools)
    -   [Spelling and Grammar Check](#spelling-and-grammar-check)
-   [Work Flow](#work-flow)

## R Code Style

To start, please follow [The tidyverse style
guide](https://style.tidyverse.org/). Lab members are welcome to deviate
slightly from it moving forward, but it has to be consistent throughout
your work.

> -   Make sure you document your code as much as possible. It’s
>     guaranteed that you won’t remember why you write some code after a
>     few days.
> -   Put all calls of an external package, i.e., `library()` to the
>     beginning
> -   Do not include `install.packages()` call in your code
> -   Generally, do not use dots in naming R objects and functions
>     (e.g., ~~`model.1`~~ → `model_1` or `model1`)
> -   Use spaces to make your code easier to read to yourself (e.g.,
>     `na.rm = TRUE` rather than `na.rm=TRUE`; see [this
>     section](https://style.tidyverse.org/syntax.html#spacing) in the
>     tidyverse style guide)
> -   Label the R code chunks

### Naming

R is notorius for not having a convention on how to name variables. Our
lab will follow the [convention in the Julia
language](https://docs.julialang.org/en/v1/manual/style-guide/index.html#Use-naming-conventions-consistent-with-Julia-base/-1).
Specifically,

-   Use lowercase letters for naming functions and names (e.g., don’t do
    `TypeI`, but use `typei`). If it’s possible to combine words without
    making it hard to comprehend, then combine them (e.g., `runmodel`,
    `simdata`, `result1`). Otherwise, use underscoe (not dot) to
    separate words in names (e.g., `extract_aic`).

### Random number generator

> Use `set.seed()` in the beginning to ensure the same numbers are
> obtained every time you run the results.

### Tools that you can use

-   [`styler`](https://style.tidyverse.org/): A package/add-in for
    automatically restyling your code according to the `tidyverse`
    style;
-   [`lintr`](https://github.com/jimhester/lintr): Automated checks to
    confirm whether your script conforms to the style guide.

### Functions

-   When possible, make sure variables inside a function are passed to
    the function as an argument, not relying on global variables. So
    instead of

use:

### Commenting

To add comment on another person’s work in Markdown/R Markdown, use

    [Mark Lai]: # (This is a comment.)

Reference:
<https://stackoverflow.com/questions/4823468/comments-in-markdown>

### Track Changes

I’m still finding a good track change package or tool for R Markdown.
One option is the
[`latexdiffr`](https://github.com/hughjonesd/latexdiffr) package, the
[`trackmd`](https://github.com/ropenscilabs/trackmd) package, and the
[`reviewer`](https://docs.ropensci.org/reviewer/) package (haven’t
tested them out).

Also `git-latexdiff`; see
<http://www.deanbodenham.com/learn/git-and-latexdiff.html>

TODO: Test out these packages.

### Git

Use Git for all lab-related projects to track changes in code files. See
<https://happygitwithr.com/>.

Generally, do not track:

-   data files or pictures that are not expected to change
-   HTML or PDF outputs that are generated from a .Rmd file (unless they
    are to be publicly shared)

#### GitHub

There are a few options for sharing Git projects, and you can use any of
them. I’ve been mostly using GitHub. The recommended workflow for
setting up a project can be found here:
<https://happygitwithr.com/new-github-first.html>

### Code Review

-   <https://www.r-bloggers.com/2020/07/best-practices-for-code-review-r-edition/>
-   <https://www.r-bloggers.com/2021/03/code-review-checklist-r-code-edition-top-3/>
-   <https://appsilon.com/write-clean-r-code/>

## Writing manuscripts

For journal/conference submissions, check the journal/conference website
for any LaTeX template. For APA style manuscripts, use the
[`papaja`](https://crsh.github.io/papaja_man/) package. Use [R
Markdown](https://rmarkdown.rstudio.com/) in general.

See the source code of some examples of published articles using
`papaja`
[here](https://crsh.github.io/papaja_man/published-manuscripts.html)

TODO: Create a template for the journal manuscript.

### Reproducibility

Use inline R code to extract numbers from results. For example, assuming
you’ve computed the mean of a variable:

``` r
set.seed(1)
y <- rnorm(10)
c(mean(y), sd(y))
```

    ## [1] 0.1322028 0.7805860

In the manuscript, do not write

``` markdown
The mean of the variable is 0.13  (SD = 0.78).
```

but write

``` markdown
The mean of the variable is `r printnum(mean(y))` (SD = `r printnum(sd(y))`).
```

#### Tables and Figures

Whenever possible, include the codes for generating a table or a figure.

Functions that can help:

-   `knitr::kable()`
-   functions in the `kableExtra` package (for conditional formatting)
-   `papaja::apa_table()`

#### Cross-Referencing

TODO: Add examples

### Citation tools

-   Mendeley (considering change to Zotero with concerns on the future
    of Mendeley)

### Spelling and Grammar Check

-   RStudio has internal spell check (Press `F7`)
-   [`gramr`](https://github.com/ropenscilabs/gramr):

## Work Flow

-   Organize each project as a RStudio project (File –> New Project)
-   Don’t do `setwd()`. Use the `here` package to locate a file for
    import ([why?](https://github.com/jennybc/here_here))

<!-- ## Posters, CVs -->
<!-- Check out the interesting [`pagedown`](https://github.com/rstudio/pagedown) package -->
