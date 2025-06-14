---
author:
- STEM Education
- Community Capitals
authors:
- STEM Education
- Community Capitals
categories:
- Week One
date: 2025-06-05
title: GROUP - Week One
toc-title: Table of contents
---

# Guidelines

Your final blog file should be `Weekly_Team_Blog.qmd` file. Don't change
the name or the GitHub Actions check will fail.

## Metadata

-   Adjust the author above so that the appropriate one of
    `"STEM Education"` or `"Community Capitals"`. is selected.
-   Change the title of the blog to "Community Capitals Week One",
    adjusting for each group. The categories are case sensitive.

## Images

Since this post doesn't specify an explicit `image` in the YAML, the
first image in the post will be used as the thumbnail of the post. You
can add a specific image in the YAML. A couple of things to remember
with linking images.

-   Place your images in the `imgs` directory. This helps prevent
    clutter and makes it easier to find the files.
-   Name your images explicitly. Don't call them `"image_1.jpg"` but
    instead something like `"age_scatterplot_1"`.
-   Don't save file names with any spaces. Add an `_` or use
    `camelCaseNaming`. Spaces will prevent the blog from properly
    rendering!
-   Make sure you follow copyright guidelines on images. Don't add
    images you would not be permitted to share in any professional
    environment.

## Data Guidelines

Here are some important things to consider when you're using data sets
in your blogs.

-   VERY IMPORTANT: All data saved in the `data` directory is publicly
    visible. Don't share data that is private into your blogs.
-   Be mindful of the size of your data. The larger the data, the longer
    it will take to render. GitHub also limits commit sizes so keep this
    in mind.
-   Save your data as an `.RDS` file when possible to save space and to
    preserve the data types of columns.

## Adding Dependencies

In order for the blogs to render on other another device we need to
ensure that the packages used to render and run the code will also be
available for others using your project. R uses a `DESCRIPTION` file to
keep track of all package dependencies, you can use the `usethis`
library to keep track of packages.

For example, if we are using the `ggplot2` library, we would run the
following.

::: cell
``` {.r .cell-code}
usethis::use_package(package = "ggplot2", type = "Imports")
```
:::

You should now be able to see `ggplot2` as an import at the bottom of
the `DESCRIPTION` file.

    Package: Weekly Blogs
    Title: What the Package Does (One Line, Title Case)
    Version: 0.0.0.9000
    Authors@R: 
        person("First", "Last", , "first.last@example.com", role = c("aut", "cre"),
               comment = c(ORCID = "YOUR-ORCID-ID"))
    Description: What the package does (one paragraph).
    License: `use_mit_license()`, `use_gpl3_license()` or friends to pick a
        license
    Encoding: UTF-8
    Roxygen: list(markdown = TRUE)
    RoxygenNote: 7.0.0
    Imports: 
        ggplot2

-   Make sure that all the packages you are using are added to
    `DESCRIPTIONS`.
    -   One way to make sure is to Restart your session and try to run
        all of your code in order to see if any library is not called
        but loaded from another session.
-   Don't include the `tidyverse` in imports, use the specific libraries
    instead.

## Using Python Code Chunks

If you are using python in your code chunks you will need to run the
following at the top of your code, after the library imports. Set the
following chunks to `eval=TRUE`.

::: cell
``` {.r .cell-code}
# Library for running python code in RStudio.
library(reticulate)
```
:::

::: cell
``` {.r .cell-code}
# Check for virtual environment, if it doesn't exist, create the venv, if it exists
# then use the venv called "r-python"

if (virtualenv_exists("r-python")) {
  use_virtualenv("r-python")
} else {
  virtualenv_create("r-python")
  use_virtualenv("r-python")
}
```
:::

::: cell
``` {.r .cell-code}
# Installing dependencies for the python virtualenv

virtualenv_install(envname = "r-python", packages = c("numpy", "pandas", "scikit-learn"), all = TRUE)
```
:::

# Markdown Resources

-   [Quarto Tutorials](https://quarto.org/docs/guide/)
-   [Quarto Websites/Blogs](https://quarto.org/docs/websites/)
-   [Quarto Markdown Reference
    Guide](https://quarto.org/docs/authoring/markdown-basics.html)
-   [RMarkdown Reference
    Guide](https://www.rstudio.com/wp-content/uploads/2015/03/rmarkdown-reference.pdf)
