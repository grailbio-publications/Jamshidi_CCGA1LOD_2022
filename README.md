## Overview

This project provides data and code to reproduce the analysis results
presented in Jamshidi A., et al., 2021. "Evaluation of Cell-Free DNA Approaches for Multi-Cancer Early Detection"

## System requirements and installation

Follow instructions at https://cran.r-project.org/bin/linux/ubuntu/README.html
to install R (version 3.6.0 was used for this analysis). The packages needed to
reproduce the results have been captured with the package `packrat`.  

To add the required packages and render the anaysis markdown:

1. Copy the contents of this package (Jamshidi_CCGA1_2021/) to the desired location.

2. Open R in the project directory.

3. Install packrat:

```
install.packages("packrat")
```

4. Install all of the versioned dependencies from CRAN and Bioconductor via packrat:

```
packrat::restore()
```

5. Render the R Markdown report containing figures and tables in the publication.  Figures
(pdf) are saved to `out/`. 

```
rmarkdown::render("Rmd/make_output.Rmd")
```

## Data

All data required to reproduce the results are provided in the directory
`data`. Each .tsv has a corresponding "dictionary" that contains definitions for each
column.

- chip_calls.tsv:        Participant-level variant information between cfDNA and WBC gDNA.
- clinical.tsv:          Clinical data table.
- lod.tsv:               LOD estimates for each Classifier.
- score_and_ctaf.tsv:    Classifier score and circulating tumor allele fraction estimates.
- score_cutoffs.tsv:     Classifier score cutoffs.
- scores_cnc.tsv:        Cancer/Non-cancer Classifier scores for each participant.
- scores_cso.tsv:        Cancer Signal Origin Classifier scores for each participant.
- umap_df_training.tsv:  UMAP components of the classifier scores for each participant.
