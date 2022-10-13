## Overview

This project provides data and code to reproduce the analysis results
presented in Jamshidi A., et al., 2022. "Evaluation of Cell-Free DNA Approaches for Multi-Cancer Early Detection"

## System requirements and installation

Follow instructions at https://cran.r-project.org
to install R (version 4.1.2 was used for this analysis). The packages needed to
reproduce the results have been captured with the package `packrat`.  Pandoc
version 2.5 was installed from https://github.com/jgm/pandoc. 
This implementation was developed and tested on Ubuntu 20.04.3 LTS.

To install the required packages and render the anaysis markdown:

1. Copy the contents of this package (`Jamshidi_CCGA1_2021/`) to the desired location (`/YOUR_LOCATION/Jamshidi_CCGA1_2021`).

2. `cd` into the project directory (`/YOUR_LOCATION/Jamshidi_CCGA1_2021`), and start `R`.

3. Install packrat:

```
install.packages("packrat")
```

4. Initialize the packrat project:

```
packrat::init()
```

Once this has completed, you must quit and restart R for the changes to take
effect (https://www.rdocumentation.org/packages/packrat/versions/0.8.0/topics/init).

5. After restarting R, confirm that the packrat library is being used by
ensuring there is a startup message like:

```
Packrat mode on. Using library in directory:
- "/YOUR_LOCATION/Jamshidi_CCGA1_2021/packrat/lib"
```

Alternatively, from the R console run `.libPaths()` and ensure that the `packrat`
library is one of the paths (i.e., something like
`"/YOUR_LOCATION/Jamshidi_CCGA1_2021/packrat/lib/x86_64-apple-darwin17.0/4.1.2"` is included).

6. Install all of the versioned dependencies from CRAN and Bioconductor via packrat:

```
packrat::restore()
```

Note some packages have dependencies on the user's local setup, and this may
necessate troubleshooting if any R packages are not able to installed on the
first attempt. For example, `RcppArmadillo` may require a user install of fortran.
These dependencies will differ based on whether run on a Linux machine vs. Mac,
which operating system is used, etc. The authors have confirmed that these R packages
can be installed and the R markdown can be rendered on both Ubuntu 20.04.3 and
macOS Monterey Version 12.5, though different user-specific local installations
were required in both cases for all packages to be installed with `packrat::restore()`.

7. Render the R Markdown report containing figures and tables in the publication.  Figures
(pdf) are saved to `/YOUR_LOCATION/Jamshidi_CCGA1_2021/out/`, and report .html is saved
to `/YOUR_LOCATION/Jamshidi_CCGA1_2021/Rmd/make_output.html`.

```
rmarkdown::render("Rmd/make_output.Rmd")
```

## Data

All data required to reproduce the results are provided in the directory
`data`. Each .tsv has a corresponding "dictionary" that contains definitions for each
column.

- chip_calls.tsv:          Participant-level variant information between cfDNA and WBC gDNA.
- clinical.tsv:            Clinical data table.
- lod.tsv:                 LOD estimates for each Classifier.
- score_and_ctaf.tsv:      Classifier score and circulating tumor allele fraction estimates.
- score_cutoffs.tsv:       Classifier score cutoffs.
- scores_cnc.tsv:          Cancer/Non-cancer Classifier scores for each participant.
- scores_cso.tsv:          Cancer Signal Origin Classifier scores for each participant.
- snv_cfdna_assay.tsv:     Sample level data for the SNV cfDNA assay.
- snv_wbc_assay.tsv:       Sample level data for the SNV WBC assay.
- umap_df_training.tsv:    UMAP components of the classifier scores for each participant.
- variant_data_hexbin.tsv: 2D hex-binned data of variant allele frequencies (%) for WBC and cfDNA.
- wgbs_assay.tsv:          Sample level data for the WGBS cfDNA assay.
- wgs_cfdna_assay.tsv:     Sample level data for the WGS cfDNA assay.
- wgs_wbc_assay.tsv:       Sample level data for the WGS WBC assay.

