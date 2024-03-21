# Demo showcasing {quarto-webr} and {quarto-shinylive} together

This repository is an example of how the [`{quarto-webr}`](https://github.com/coatless/quarto-webr) 
and [`{quarto-shinylive}`](https://github.com/quarto-ext/shinylive) Quarto extensions can be used together. 

## Installation 

Please make sure to create a Quarto project and, then, install each extension inside of Terminal:

```sh
# For shinylive
quarto add quarto-ext/shinylive

# For quarto-webr
quarto add coatless/quarto-webr
```


Both extensions should be found in `_extensions` within the project directory. If not, please double-check your working project directory.

## Quarto Document

From there, please setup a Quarto document (`.qmd`) that contains:

1. the Shiny app source inside of a code cell denoted with `{shinylive-r}`; and,
2. the code you want webr to use with `{webr-r}`.

Here is an example skeleton Quarto document that has both code cells present: 

````md
---
title: Pairing {quarto-shinylive} and {quarto-webr}
format:
  html:
    resources: 
      - shinylive-sw.js
engine: knitr
filters:
  - webr
  - shinylive
---

## {quarto-shinylive}

```{shinylive-r}
#| standalone: true
library(shiny)

ui <- fluidPage(
   titlePanel("Hello Shiny!")
)

server <- function(input, output, session) {
  # code
}

shinyApp(ui, server)
```

## quarto-webr

```{webr-r}
print("hello quarto-webr world!")
```

````
