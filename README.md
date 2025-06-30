# Project: Impact of Motherhood with Young Children on Employment Status (US 2023 Data)
**Author**: Amber Ni 
| **Date**: 04-30-2025 | **Course**: Jobs, Workers, Development

## Project Description
This project analyzes IPUMS USA data from 2023，with selected variables related to employment status, demographic indicators and the presence of young children. It primarily focuses on identifying **key trends in the employment status of women with young children under age 5 across different demographic groups**, and examines **the correlation between having young children and employment outcomes**. Conducted in **Python**, the project involves data cleaning, variable selection, and both descriptive and regression analyses to explore relationships between these variables and their potential correlates. 

The repository **includes**: 
- raw dataset
- Python notebooks (Google Colab)
- Project report
- Folder containing all visualizations included in the report

This work aims to explore the current relationship between motherhood and employment status using 2023 data to assess whether mothers, particularly those with younger children, continue to face employment disadvantages compared to women without children in the U.S.

## How to Use This Repository

If you'd like to **run the analysis** on your own laptop, follow these steps:
1. Clone this repository or download the files to your local machine (or upload them to your Google Drive if using Colab).
2. Ensure the raw dataset file is named `cps_00002.dta`. Place it in the same directory or your Google Drive folder where the notebook expects to read it.
3. Open the provided Python notebook in Google Colab.
4. If using Google Colab:
   - Mount your Google Drive with `drive.mount('/content/drive')`.
   - Adjust the file path in `pd.read_stata()` if your Drive structure is different, e.g.: `df = pd.read_stata('/content/drive/My Drive/your_folder/cps_00002.dta')`
5. Run the notebook cells sequentially to perform data cleaning, analysis, and generate visualizations.

If you're only **interested in viewing the code and report**: Simply download or browse all the documents in this repository.

This workflow allows you to reproduce all analyses and figures included in the project report.

## Research Question
Do mothers, particularly those with younger children, work fewer hours or have lower employment rates compared to women without children in the U.S.?

## Data Source

I identified key variables relevant to this research question from the 2023 survey data and downloaded a customized dataset from IPUMS USA: https://usa.ipums.org/usa/.

This dataset includes 27 variables and 146,133 observations.

Key variables used in this analysis:
* `relate`: relationship to household head
* `age`: age
* `sex`: sex
* `race`: race
* `marst`: marital status
* `nchild`: number of own children in household
* `nchlt5`: number of own children under age 5 in household
* `ynch`: age of youngest own child in household
* `empstat`: employment status
* `labforce`: labor force status
* `educ`: educational attainment recode
* `schlcoll`: school or college attendance

## Workflow
1. **Download Datasets** 
   - Select relevant variables and download dataset from IPUMS USA.
3. **Confirm Variables of Interest** 
   - Dependent Variable: `empstat` - employment status (employed vs. unemployed). 
   - Main Variable of Interest: `nchlt5` - the number of own children under age 5 in the household
   - Control Variables: region (`region`), age (`age`), race (`race`), marital status (`marst`), and educational attainment (`educ`)
6. **Data Preparation** 
   - Inspect Variables: Check data types, distributions, and completeness. 
   - Clean Variables: Recode/rename where necessary, handle missing data, and correct errors. 
7. **Descriptive Analysis**  
   - Visualize trends and patterns using bar and line charts.
8. **Regression Analysis** 
   - Perform logistic regression model to explore relationships between variable of interest and dependent variable.
   - Interpret coefficients and statistical significance.
9. **Report Writing** 
   - Export visualizations and write report on typora.
     
## Main Results

Having one child under age 5 is correlated with a 21% higher probability of being employed compared to having no young children, suggesting a potential link between childcare responsibilities and increased labor force participation for women with a single child. As the number of young children increases, the coefficients become statistically insignificant.

While there are promising signs that having young children may encourage women to participate in the labor force, the effects vary significantly across different demographic groups. These disparities highlight the need for
targeted policy interventions to ensure equitable support for women facing childcare especially for young children and employment challenges.

## Limitations

1. This project only includes a limited set of control variables (region, age, race, marital status, and education), which means other potential confounders that could influence both the likelihood of having young children and employment status may be omitted, potentially biasing the correlation.
2. Many of the regression results are not highly statistically significant (p-values are not very small), suggesting the conclusions are not strongly supported by the data and would benefit from additional variables and larger sample sizes in future research.
3. The analysis relies solely on data from 2023, providing only a cross-sectional snapshot, which limits the ability to assess trends or changes over time.

