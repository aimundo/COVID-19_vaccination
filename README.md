Differences in COVID-19 vaccination in the province of Ontario across Health Regions and socio-economic strata
====================================================================================================================================

[![License: CC BY 4.0](https://img.shields.io/badge/License%20All-CC%20BY%204.0-lightgrey)](https://creativecommons.org/licenses/by/4.0/) [![License: CC0-1.0](https://img.shields.io/badge/License%20Parts-CC0%201.0-lightgrey)](http://creativecommons.org/publicdomain/zero/1.0/)



This repository contains all the code and data used to create the manuscript, which is available as a preprint here. This paper explores COVID-19 vaccination in the province of Ontario, Canada.

# How to use this repository

The best way to reproduce the paper and its results is to fork this repository and follow the instructions below.

# Repository organization

The repository contains different directories that work in conjunction to create the final manuscript. The directories are:

- `code`: Contains all R scripts for statistical analyses, map creation, and data cleaning.
- `data`: Cotnains files (in csv format) with the data used for analysis.
- `manuscript`: Quarto files (*.qmd) used to create the different manuscript sections.

## Code

The directory `code` contains scripts used to create the manuscript. All these files need the libraries that appear in the first chunk in `main.qmd` in the `manuscript` directory. Therefore if individual scripts need to be run, the required libraries need to be loaded first.

- `data_reparation.R`: script to clean the data and prepare for analysis.
- `raking.R`: script to correct the data using Census estimates.
- `regression.R`: script that creates two logistic regression models (corrected and uncorrected).
- `uncorr_model.R`: from the model for uncorrected data in `regression.R` this script creates the figure from the paper.
- `corr_model.R`: from the model for corrected data in `regression.R` this script creates the figure from the paper.

## Data

This directory contains the data files used to create models, obtain geographical information. The files in this directory are:

- `FieldsBehaviouralSurveyRawDataV2V3.xlsx`: Raw file from the Fields COVID-19 Attitudes survey. Includes a data dictionary for all the questions deployed in the survey.
- `Fields_data.csv`: This is a csv file created from the file above to be used for the analysis in the manuscript.
- `municipalities_clean.csv`: File with the name of the majority of the municipalities in the raw datafile, along with their full title (e.g. Township, Municipality), and the geographical region the municipality belongs to (District, County, etc).
- `missing_municipalities_updated_May_05_2023.csv`: this file has the municipalities missing from `municipalities_clean.csv` with the information in each case manually added.
- `geographic_areas.csv`: Contains information for all the geographical areas of Ontario, indicating the type of area (County, Regional Municipality, District).
- `Consolidated_LTC_dataset.csv`: Data from this website on Long-Term Care Homes for seniors in Ontario, from [this site](https://paulallen.ca/consolidated-dataset-of-ltc-homes-in-ontario/). This file was used to match each city from the Fields Survey to its corresponding Local Health Integration Network (LHIN).
- `missing_health_regions_updated_May_05_2023.csv`: File created manually for those cities from the Fields Survey dataset that were not present in Long-Term Care Home dataset. Corresponding LHIN in each case was manually added.

Additionally, the directory `map_data` can be found here, where shp files needed to create the map in the manuscript are to be placed (these files are not included because they are too large for the GitHub repository, but the script `map_June_01.R` in the `code` directory contains instructions on how to download and process the data to create the map. The map created by `map_June_01.R` is `map_June_01.pdf`, which is the only file present in the directory.

## Manuscript
The different manuscript sections can be found in the `manuscript` directory, which contains:

- `01-background.qmd`: first part of the manuscript.
- `02-methods.qmd`: describes the methods used in the paper and imports a map of Ontario where the different Health Regions and the observations obtained from each city are presented.
- `03-results.qmd `:  contains a descriptive table of the data used in the manuscript, and the results of the statistical analyses. 
- `04-discussion.qmd`: discussion.
- `05-conclusion.Rmd`: conclusion to the manuscript.


# Instructions

This work was created using R. Therefore, you need to install the latest version of R. Additionally, it is recommended that and IDE such as RStudio is installed as well. Directions to install R and RStudio can be found [here](https://rstudio-education.github.io/hopr/starting.html). <br>

After installing R and RStudio, you need to install the {quarto} and {tinytex} (a LaTeX distribution) packages in order to be able to compile the manuscript in PDF. Instructions to install `quarto` can be found [here](https://quarto.org/docs/get-started/).<br>
Instructions to install {tinytex} can be found [here](https://yihui.org/tinytex/). Note that you have to install the package and then run the command `install_tinytex()` to make it work.

All the required libraries to run the code and create the manuscript can be found in the first code chunk in the file`main.qmd`,which calls all the files to generate the main manuscript). If using RStudio, the first time you open `main.qmd` you should automatically receive a warning about the missing packages that need to be installed; you can choose to install all the missing packages then.

Although individual code chunks can be run, it is advised to first generate a document by knitting `main.qmd`. If individual chunks of code want to be examined, it is best to open the `.qmd` file of interest and see the code structure to the different functions scripts found in the `code` directory.


This work has an appendix, which can be re-created by knitting the file `appendix.qmd`, which can be found in the `manuscript` directory. 

The appendix is a stand-alone document that can be compiled independently from the main manuscript. In this way, the reader chooses the section of interest and can examine and run the code independently.



The repository also contains directories `references` for references used in the main manuscript, `latex` for LaTeX compilation.

# License

This entire repository is licensed under a CC BY 4.0 License, which allows reuse with attribution. However, certain files are released under the CC0 1.0 public domain dedication. The files indicated below are dual licensed under CC BY 4.0 and CC0 1.0:

- `02-Challenges.Rmd`
- `03-GAM Theory.Rmd`
- `04-Longitudinal analysis with GAMs`
- `07-Appendix.Rmd`

All other files are under CC BY 4.0.

# Contact

If you have questions or comments please contact Ariel Mundo (ariel.mundo.ortiz@umontreal.ca)
