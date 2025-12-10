# Crime, Commissions, and Citizen Reporting: Evidence from Marikana

## Abstract
In August 2012, a wildcat strike by mineworkers at the Lonmin platinum mine in Marikana, North West Province, escalated into a confrontation between workers and the South African Police Service. On 16 August 2012, police opened fire on striking miners, killing 34 and injuring dozens more in what became the most lethal use of state force in democratic South Africa. The scale of the violence, its extensive media coverage, and public outrage prompted the government to establish the Marikana Commission of Inquiry to investigate the actions of the police, the mining company, unions, and the state. This project investigates whether the Marikana Commission of Inquiry (2012–2015) altered patterns of crime reporting and police activity in the Rustenburg area of South Africa. Specifically, it asks:
- Did the Commission affect the volume of crime reported by citizens?
(Measured as the sum of all contact crimes, contact-related crimes, property crimes, and other serious crimes reported to SAPS.)
- Did the Commission change levels of police operational activity?
(Measured using crimes dependent on police action for detection as a proxy for proactive policing.)
These questions speak to the broader issue of whether large-scale public inquiries influence institutional behaviour, citizen trust in formal systems, and the functioning of state accountability mechanisms. To estimate the causal effect of the Marikana Commission, the project uses a difference-in-differences (DiD) and an interrupted time series (ITS) identification strategy.

## Data Source: 
South African Police Service. South African Police Service Annual Crime Records 2008-2023 [dataset]. Version 1. Pretoria: South African Police Service (SAPS) [producer], 2023. Cape Town: DataFirst [distributor], 2025. DOI: https://doi.org/10.25828/5MAW-4H90

## How to Replicate
1. Ensure you have Python 3 installed and the required libraries

   ```bash
   pip install seaborn statsmodels pandas matplotlib.pyplot numpy stargazer
   ```

2. Open `NB01-Data-Transformation.ipynb` in a Jupyter environment (VS Code or Jupyter Notebook).

3. Run all cells in `NB01` to transform, filter and categorise the crime data for Rustenburg Municipality. This will create the file `data/expanded_crime_data.csv`.

4. Open `NB02-Regression-Model.ipynb` and run all cells to perform the regressions. This will:

   - Regress total police activity on the difference-in-difference estimator and all relevant controls
   - Do a parallel trends check for police activity in the treated and control group
   - Regress total citizen reported crime on the difference-in-difference estimator and all relevant controls
   - Do the interrupted time series for Rustenburg Municipality for the citizen model and the police model
   - Generate the model summaries for all the aforementioned regressions under `/model-summaries`

5. Open `NB03-Charts.ipynb` and run all cells to plot the two models. This will:
   - Plot the total citizen reported crime (the citizen model) from 2008 to 2023 for the treated and control group.
   - Plot the total police activity (the police model) from 2008 to 2023 for the treated and control group.
   - Save the charts for all the aforementioned plots under `/charts`

