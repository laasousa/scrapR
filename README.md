# scrapR

`R` package to extract data from PDF figures

## Installation

The easiest way to install the development version of `scrapR` is to use the `devtools` package:

```r
# install.packages("devtools")
library(devtools)
install_github("adamkucharski/scrapR")
library(scrapR)

# load dependencies
# install.packages("tidyverse")
# install.packages("grImport")
library(tidyverse)
library(grImport)

```

## Example

First we need a figure to extract data from. You can use `simulate_data()` to generate a simulated figure if needed.

![Alt text](data/figure0.pdf "Title")

Before extracting data, it's worth removing unnecessary parts of the vector graphic. Create a copy of your plot in Affinity/Illustrator and delete everything except the lines with data you want and four tick marks (2 on x-axis, 2 on y-axis) that will be used to calibrate the scale.

Navigate to the directory containing the simplified figure and import the data

```r
load_data(file_name="[FIGURENAME].pdf")
```

This will output a raw RDS file and a figure (`[FIGURENAME].guide.pdf`) with the different components labelled with letters. If the tick marks are not labelled as "A,B,C,D" in some order, edit `[FIGURE NAME].guide.csv` so the letters match up with your orignal four tick marks.

Then extract the data using the RDS file and guide CSV file:

```r
extract_data(file_name = "figure1.pdf")
```