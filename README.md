PM2.5 and Breast Cancer Incidence Across California Counties

## Introduction

Among women, breast cancer is the most commonly diagnosed cancer and the leading cause of cancer-related death globally, and in the United States incidence rates increased by approximately 0.5% annually from 2010 to 2019.
In California, age-adjusted breast cancer incidence rates vary widely across counties, ranging from 150.6 cases per 100,000 women in Marin County to 55.9 cases per 100,000 women in Modoc County, demonstrating substantial geographic variation.
At the same time, county-level air pollution exposure also varies across the state. Fine particulate matter (PM2.5) refers to airborne particles smaller than 2.5 micrometers in aerodynamic diameter that originate from sources such as motor vehicle exhaust, combustion processes including oil and coal burning, wood smoke, vegetation fires, and industrial emissions.
Most existing research has focused on PM2.5 exposure and lung cancer, but emerging evidence suggests that long-term exposure to air pollution may contribute to systemic inflammation, oxidative stress, and DNA damage, which are biological mechanisms also relevant to breast carcinogenesis.
A potential biological mechanism is that prolonged exposure to fine particulate matter leads to oxidative stress and inflammation, which can damage DNA and increase the likelihood of mutations in tumor suppressor genes such as BRCA1 and BRCA2. Because BRCA1 and BRCA2 play essential roles in DNA repair, mutations in these genes can impair genomic stability and increase susceptibility to breast cancer.
Additionally, environmental exposures may interact with genetic susceptibility and contribute to disparities in cancer risk across racial and ethnic groups.
Therefore, this study examines whether county-level PM2.5 concentrations are associated with age-adjusted breast cancer incidence rates in California.

## Research Question

Is county-level average PM2.5 concentration associated with age-adjusted breast cancer incidence rates across California counties from 2018–2022?

## Methods

### Study Design

This study uses an ecological design to examine whether county-level air pollution is associated with breast cancer rates in California.
Ecological studies examine characteristics of environments and populations to understand human systems and environmental health. This design is particularly useful for examining population-level patterns, health inequities, and geographic differences that may be relevant to public health policy.
The unit of analysis is the county, meaning that both air pollution and breast cancer data are analyzed at the population level rather than at the individual level.
This approach allows larger geographic patterns across the state to be identified, but it does not allow conclusions about individual exposure or prove direct causation.

### Variables

The independent variable is the average annual PM2.5 concentration for each county from 2018–2022, measured in micrograms per cubic meter.
The dependent variable is the age-adjusted breast cancer incidence rate for each county from 2018–2022, measured as cases per 100,000 women.
Age-adjusted rates were used so that counties could be compared more accurately because each county has a different age distribution.

### Data Sources

PM2.5 data were collected from publicly available environmental health datasets from the U.S. Environmental Protection Agency (EPA).
California county-level breast cancer incidence data were obtained from the National Cancer Institute's State Cancer Profiles database.
Each county's PM2.5 level was matched with its corresponding breast cancer incidence rate using FIPS (Federal Information Processing Standards) numbers. FIPS numbers contain two digits representing the state and three digits representing the county.

### Data Processing

The breast cancer dataset provides cumulative age-adjusted incidence over five years, while California releases air pollution data for individual years.
To better align exposure with the outcome, PM2.5 data were obtained by county for each year from 2018–2022 from the EPA's national datasets. The five annual tables were merged and a five-year average PM2.5 concentration was calculated for each county.
The air pollution data required substantial processing because the five annual datasets contained measurements for counties throughout the United States and included parameters other than PM2.5.

The main processing steps were:
1. Selecting the necessary columns, including State Name, County Name, Year, Parameter Name, Arithmetic Mean, County Code, and State Code.
2. Combining the five annual datasets and identifying the year associated with each measurement.
3. Filtering the combined dataset to California and PM2.5.
4. Using the state and county codes to construct FIPS numbers.
5. Calculating annual county-level PM2.5 averages.
6. Calculating the five-year average PM2.5 concentration for each county.
7. Processing the California breast cancer incidence dataset to isolate the necessary variables and ensure the data were aligned.
8. Merging the breast cancer and PM2.5 datasets using FIPS numbers.
9. Checking that the county-level observations were correctly matched.
10. Removing observations with missing values.
    
The final dataset contained 47 California counties with no missing values, which were also categorized as rural or urban.


### Statistical Analysis

Descriptive statistics and visualizations were used to examine the distribution of PM2.5 levels and breast cancer rates across California counties.
A Pearson correlation test was used to examine whether higher air pollution levels were associated with higher breast cancer incidence rates. Pearson correlation is appropriate for examining the relationship between two continuous variables.
The correlation produces an R-value, which describes the strength and direction of the relationship, and a p-value, which was used to evaluate statistical significance.
The relationship was also visualized using a linear regression model and scatterplots. Additional visualizations examined geographic patterns in breast cancer incidence and PM2.5, as well as rural/urban differences.

## Results

The Pearson correlation between age-adjusted breast cancer incidence rates and five-year average PM2.5 concentration was:
r = -0.4136542
This represents a moderate negative correlation, suggesting that counties with higher average PM2.5 concentrations tended to have lower recorded breast cancer incidence rates in this dataset.
The analysis produced a p-value below 0.05, indicating that the observed correlation was statistically significant according to the significance threshold used in the analysis.
These findings rejected the original hypothesis that higher county-level air pollution would be associated with higher breast cancer rates.

## Discussion

One possible explanation for the negative correlation is confounding by wealth gaps and socioeconomic inequity across different areas of California.
Areas with high air pollution may also experience poorer access to healthcare and infrastructure. Therefore, counties with higher levels of air pollution may have lower recorded breast cancer incidence because of reduced access to preventative healthcare and screening.
Conversely, areas with lower pollution may have better healthcare infrastructure and greater access to mammography screening, resulting in more breast cancer cases being detected and recorded.

### Exploratory Mammography Analysis

To further investigate this possibility, mammography screening rates were compared with PM2.5 levels for 45 of the 47 counties included in the analysis.
The correlation between PM2.5 and mammography screening rates was:

r = -0.3959 with a p-value of 0.007796.

Mammography rates decreased as air pollution increased, while breast cancer incidence also decreased as mammography rates decreased. This provides one possible explanation for why breast cancer incidence decreased as air pollution increased in the primary analysis.
However, this exploratory analysis does not establish that differences in screening caused the observed relationship. This is separate from the primary R Markdown analysis. Instead, it is provided as a supplementary Excel analysis.

### Limitations

Several limitations should be considered.
1. The analysis is based on county-level data rather than individual-level exposure.
2. County-level analysis cannot explain individual exposure in relation to breast cancer.
3. The breast cancer and air pollution timelines do not exactly match because breast cancer incidence was provided as a five-year cumulative rate while PM2.5 data were available annually.
4. Breast cancer has a latency period, meaning that the effects of air pollution exposure may not appear in breast cancer incidence during the same period.
5. The analysis did not account for all other factors that could affect breast cancer incidence.
6. Socioeconomic conditions, healthcare access, screening rates, and other demographic and environmental factors may confound the observed relationship.
7. Data collection was limited to publicly available online datasets.
7. Because this is an ecological observational study, the observed correlation should not be interpreted as evidence that PM2.5 causes or prevents breast cancer.
   
## Reproducibility

This primary analysis was conducted in R/RStudio using R Markdown. The analysis code, rendered HTML report, and generated figures are included in this repository. There is also a supplementary exploratory mammography analysis in the form of a Excel worksheet.
The EPA AirData files are large datasets and are therefore not stored directly in the repository. Instead, the R Markdown analysis automatically downloads and unzips the required 2018–2022 EPA datasets when they are not already present in the project's data/ directory.
The breast cancer incidence dataset used in the analysis is included in the repository.
This structure allows the analysis to be reproduced using the publicly available source data and the included R Markdown code.

## Repository Structure

```text
pm25-breast-cancer-analysis/
│
├── analysis/
│   ├── Data analysis.Rmd
│   └── Data analysis.html
│
├── data/
│   └── incd.csv
│
├── supplementary_analysis/
│   └── mammography_analysis.xlsx
│
└── figures/
    ├── breast_cancer_pm25_scatter.png
    ├── breast_cancer_pm25_scatter_labeled.png
    ├── breast_cancer_california_map.png
    ├── pm25_california_map.png
    ├── breast_cancer_pm25_scatter_rural_urban.png
    └── rural_urban_pm25.png
```
   
## Tools

The analysis was performed in R using packages including:
tidyverse
stringr
dplyr
ggplot2
ggrepel
sf
tigris

