**NOTE:** this repo is now part of [breakinspectoR](https://github.com/roukoslab/breakinspectoR). The code here has been frozen as of November 2024, and additional features are available only in breakinspectoR.

# bluntPred

Prediction of blunt rates of Streptococcus pyogenes Cas9 (SpCas9) using the XGBoost model trained with HiPlex1 data.

## Install

### Dependencies

The main dependency is [H2O](https://h2o.ai/).

Remove any previously installed H2O packages for R.

```R
if ("package:h2o" %in% search()) { detach("package:h2o", unload=TRUE) }
if ("h2o" %in% rownames(installed.packages())) { remove.packages("h2o") }
```

Download packages that H2O depends on.

```R
install.packages(c("RCurl","jsonlite"))
```

Download and install the H2O package for R. The models were trained on H2O version 3.36.1.2, therefore specifically install this version.

```R
install.packages("h2o", type="source", repos="http://h2o-release.s3.amazonaws.com/h2o/rel-zumbo/2/R")
```

Test the H2O installation with:

```R
library(h2o)
localH2O = h2o.init()
demo(h2o.kmeans)
```

Now, it's all set to install the package.

### Installing the package

The package resides in GitHub only. You will probably need `devtools` for that (`install.packages("devtools")`).

```R
devtools::install_github("roukoslab/bluntPred")
```

## Run

Open the web app in your R console:

```R
bluntPred::shiny_bluntPred()
```

Paste a list of gRNAs targets and click on `Predict`.
The list can actually be a table with \<tab\> or \<comma\> separated fields.
The gRNA sequence is expected to be in the *first* column.

NOTE: Only the seed portion of the protospacer (this is, the last 10 nucloetides of the target sequence) are used for the prediction in this model.

## Cite

If you find this tool useful and use it in your research, please cite our publication:

Longo, Sayols et al., Linking CRISPR–Cas9 double-strand break profiles to gene editing precision with BreakTag. Nat. Biotechnol. 2024. DOI: https://doi.org/10.1038/s41587-024-02238-8
