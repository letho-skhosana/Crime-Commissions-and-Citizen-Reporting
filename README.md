# Crime, Commissions, and Citizen Reporting: Evidence from Marikana

## Context
In August 2012, a wildcat strike by mineworkers at the Lonmin platinum mine in Marikana, North West Province, escalated into a confrontation between workers and the South African Police Service. On 16 August 2012, police opened fire on striking miners, killing 34 and injuring dozens more in what became the most lethal use of state force in democratic South Africa. The scale of the violence, its extensive media coverage, and public outrage prompted the government to establish the Marikana Commission of Inquiry to investigate the actions of the police, the mining company, unions, and the state.

## Research Question
This project investigates whether the Marikana Commission of Inquiry (2012–2015) altered patterns of crime reporting and police activity in the Rustenburg area of South Africa. Specifically, it asks:
Did the Commission affect the volume of crime reported by citizens?
(Measured as the sum of all contact crimes, contact-related crimes, property crimes, and other serious crimes reported to SAPS.)
Did the Commission change levels of police operational activity?
(Measured using crimes dependent on police action for detection as a proxy for proactive policing.)
These questions speak to the broader issue of whether large-scale public inquiries influence institutional behaviour, citizen trust in formal systems, and the functioning of state accountability mechanisms.

## Identification Strategy
To estimate the causal effect of the Marikana Commission, the project uses a difference-in-differences (DiD) strategy leveraging variation across police stations within the Rustenburg Municipality.
* **Treatment and Control Groups**:
Treatment group: The Marikana police station, which is the only station directly implicated in the Marikana massacre and the focal point of the Commission of Inquiry.
Control group: Police stations within Rustenburg Municipality that were not involved in the Marikana Massacre and were not the primary focus of Commission testimony or public attention. These stations share the same municipal governance, regional policing structures, and socioeconomic context, making them credible controls. These stations included Bethanie, Boitekong, Boons, Lethabong, Phokeng, Rustenburg, and Tlhabane.
* **Treatment Timing**:
The Commission began in October 2012, ran through 2013–2014, and released its final report in June 2015.
For estimation, treatment begins in 2012 and ends in 2015.
* **Assumptions and Credibility**:
Parallel trends: In the absence of the Commission, treatment and control stations would have followed similar trends in crime reporting and police activity. This is tested using pre-treatment parallel trends plots in the notebook.
The Commission was exogenous to station-level crime trends – it resulted from a quasi-random singular national event, not from crime fluctuations.
All stations are within the same local municipality, limiting confounding factors from demographic or governance differences.
No spillovers: Crime reporting patterns in control stations were not directly influenced by the Commission or media/public reaction as this was focused on the actions of police in the marikana massacre only.
All station-specific and time-specific factors – such as fixed station characteristics, municipality-wide shocks, and broader macro conditions – are absorbed through station and year fixed effects. In addition, when modelling police activity, total citizen-reported crime is controlled for (and vice versa), ensuring that broader fluctuations in overall crime levels do not confound the estimated treatment effect.

## Data
* **Data Sources**: South African Police Service. South African Police Service Annual Crime Records 2008-2023 [dataset]. Version 1. Pretoria: South African Police Service (SAPS) [producer], 2023. Cape Town: DataFirst [distributor], 2025. DOI: https://doi.org/10.25828/5MAW-4H90
* **Data Storage**: The SAPS data was kept in its original CSV format to preserve it as a reference point. Although I filtered, categorised, and transformed the data to isolate data for Rustenburg Municipality in order to run the relevant regressions.
* **Crime Categories**: The SAPS has a list of crime categories that I used to sort the data. They are:
Contact crimes: These crimes involve the use of violence or a threat to use violence that is directed against the person of a victim.
Contact-related crimes: These crimes occur in the absence of the victim or under circumstances in which the victim is unaware of the crime being committed at the time (no person is directly or immediately harmed or threatened during the commission of such a crime).
Crimes against property:  These are violent crimes committed against material assets with the intention to cause damage and or the destruction of another person’s property.
Other serious crimes: The category includes all theft not mentioned elsewhere (common or other theft), commercial crime (fraud-related crimes) and shoplifting. 
Crimes dependent on police action for detention: These are crimes in general not reported by members of the public, but mainly detected through direct police action, such as roadblocks and SAPS intelligence-led operations.
* **Important Note**: In charts and regression summaries, a singular year date is used instead of the fiscal year date. This is for readability purposes, but that date still measures that fiscal year. So a date saying 2012, will be measuring the fiscal year from March 2012 to February 2013.

## Summary of Results
Across citizen-reported crime, the analysis finds no strong evidence that the Marikana Commission produced a significant or lasting change in reporting patterns within Rustenburg Municipality. Reporting trends in treated and control police stations remain broadly parallel before, during, and after the Commission period, suggesting limited behavioural change on the part of citizens in how they engage with the police.
In contrast, police activity shows a large and distinct decrease during the years in which the Commission was active, as measured by crimes dependent on police action for detection. This decline indicates a substantial short-run reduction in proactive policing or detection-driven operations in the treated station at the height of scrutiny and institutional pressure. However, the effect does not persist: police-detected crime converges with control group levels after the inquiry concludes, implying that changes in police behaviour were temporary and tied specifically to the Commission period rather than reflective of a long-term shift.

## How to Replicate
1. Ensure you have Python 3 installed and the required libraries

   ```bash
   pip install seaborn statsmodels pandas matplotlib.pyplot numpy
   ```

2. Open `NB01-Data-Transformation.ipynb` in a Jupyter environment (VS Code or Jupyter Notebook).

3. Run all cells in `NB01` to transform, filter and categorise the crime data for Rustenburg Municipality. This will create the file `data/rustenburg_municipality_crime_data.csv`.

4. Open `NB02-Regression-Model.ipynb` and run all cells to perform the regressions. This will:

   - Regress total police activity on the difference-in-difference estimator and all relevant controls
   - Do a parallel trends check for police activity in the treated and control group
   - Regress total citizen reported crime on the difference-in-difference estimator and all relevant controls
- Do a parallel trends check for citizen reported crime in the treated and control group
   - Generate the model summaries for all the aforementioned regressions under `/model-summaries`

5. Open `NB03-Charts.ipynb` and run all cells to plot the two models. This will:
   - Plot the total citizen reported crime (the citizen model) from 2008 to 2023 for the treated and control group.
   - Plot the total police activity (the police model) from 2008 to 2023 for the treated and control group.
   - Save the charts for all the aforementioned plots under `/charts`

