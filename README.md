# Hill RTS-s immune development code

Supporting code for Hill et al. "Immune system development varies according to age, location and anemia in African children"


## Introduction

This code outlines the analyses behind various figures in the paper.

This is a github mirror of an RStudio project.

The relevant data is supplied in the folder `/data`

Html output is provided in the folder `/html`. Knitting the provided Rmarkdown files (.Rmd) here will re-generate these html files in the project directory. The contents of `/html` are difficult to view on github.com (it does not render the html) - the RStudio viewer will render these so you can compare your local results to our own. 

R  packages are managed by the packrat package manager, so the end-user can install this repository on their local machine on a 'fresh' version of R/Rstudio. Source code packages are included, which should work on Windows/OSX/Unix. We have tested OSX and Unix. Use `packrat::status()` and `packrat::restore()` before trying to run the .Rmd files.

## Workflow [for novices]

1. Install RStudio https://rstudio.com/products/rstudio/download/

 - tested with Rstudio 1.2.5019 and R 3.6.1

2. Install git, either via:

i. https://git-scm.com

ii. or, **if you do not have administrator rights**, via `conda` (which does not require admin rights to install)

- follow miniconda2 installation guide for your OS eg https://conda.io/projects/conda/en/latest/user-guide/install/macos.html
  
  - you can use alternative versions of conda. Be aware that sup code D will need to be alternately configured so that R can 'see' your installation of python and reticulate library.
   
  - for OS X 10.14.6 (testing machine), python2 is default so miniconda2 used.

- to add git to your <base> environment, run `conda install git` in Terminal (or its equivalent in your OS)

3. Follow RStudio's guide to pull this project from GitHub into a new project.

4. Install the included packages, by running the following in RStudio console: `packrat::status()` and `packrat::restore()`. The restore process takes several minutes.

5. Knit the accompanying Rmd files


## Additional considerations

### 1. To run supplementary code C, you need to obtain permission to use the GenR dataset.

Raw data for the Dutch Generation R cohort is available upon collaboration request (https://generationr.nl/researchers/collaboration/)
Contact details: 
Prof dr. Henriette Moll h.a.moll@erasmusmc.nl
Prof.dr. Menno van Zelm menno.vanzelm@monash.edu

"GenR.common" file preprocessing: 
The absolute counts for Generation R data were transformed into "% of parent" frequencies (e.g. "CD4+ T cell", "CD8+ T cells" of "CD19+ B cell") in order to be comparable to the Tanzanian data. The 19 cell types that were comparably gated between the two cohorts were used. Refer to GCRF.GenR for these cell-type names. 
Convert GenR month of age to "ageAtVisit" variable in weeks. 


### 2. To run supplementary code D, the required R packages need gfortran to compile amd mofapy to run.

- gfortran
  - gfortran is not present on a fresh OSX install
  - gfortran is available via conda eg `conda install gfortran_osx-64` in Terminal

- mofapy
  - the python library mofapy is available on the bioconda channel, with the following Terminal commands:
  - `conda config --add channels bioconda`
  - `conda install mofapy`
  - there are several dependencies that are also installed, so this can take a few minutes to complete.
  - if you are using an alternative installation of conda, python or mofapy see the MOFA vignette to configure
