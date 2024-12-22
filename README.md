# Analysis of Airport Complaints from Individuals with Disabilities
### Project Overview
This project involves analyzing complaints from individuals with disabilities at various airports in the United States. The data was collected on behalf of the American Association of People with Disabilities (AAPD) to identify trends in complaints and provide insights into areas for improvement in airport services and accessibility.

### Requirements
To run the code and perform analysis, you'll need the following Python libraries:
- pandas
- numpy
- matplotlib
- plotly
- seaborn
You can install these libraries using pip:
```bash
pip install pandas numpy matplotlib plotly seaborn
```
### Data Files
The project relies on the following CSV data files:
- complaints-by-airport.csv: Contains complaints by airport.
- complaints-by-subcategory.csv: Contains complaints by subcategory.
- iata-icao.csv: Contains IATA and ICAO codes for airports.
- complaints-by-category.csv: Contains complaints categorized by different criteria.
### Setup
Load Data: Import the necessary libraries and load the data from the CSV files.
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

complaints_airport = pd.read_csv('complaints-by-airport.csv')
complaints_subcat = pd.read_csv('complaints-by-subcategory.csv')
iata_icao = pd.read_csv('iata-icao.csv')
complaints_cat = pd.read_csv('complaints-by-category.csv')
```
### Data Cleaning and Preprocessing: Clean and process the data to make it ready for analysis.
- Remove missing values (dropna())
- Filter out complaints based on thresholds (>100, >10, <10)
- Merge dataframes for better analysis
```python
complaints_cat_wo_na_airports = complaints_cat.dropna()
complaints_subcat_wo_na_airports = complaints_subcat.dropna()
```
### Data Analysis: Perform analysis on the complaints data.
- Analyze complaint counts across airports
- Identify airports with the most and least complaints
- Filter complaints related to individuals with disabilities
```python
complaints_cat_disability = complaints_cat_wo_na_airports[complaints_cat_wo_na_airports['clean_cat'].isin(['Persons w/ Disabilities (PWD)'])]
complaints_subcat_disability = complaints_subcat_wo_na_airports[complaints_subcat_wo_na_airports['clean_cat'].isin(['Persons w/ Disabilities (PWD)'])]
```
### Visualization: Visualize the results using plotly, seaborn, and matplotlib.
- Create choropleth maps for complaints by state
- Plot complaints by subcategory, state, and year
```python
Copy code
import plotly.express as px

fig = px.choropleth(state_totals_df, locations='state', locationmode="USA-states", scope="usa", color='count')
fig.show()

sns.barplot(data=disability_complaints, x='month', y='count')
sns.lineplot(data=disability_complaints, x='year', y='count')
```
### Key Insights
- Airports with the most complaints from individuals with disabilities are identified.
- Breakdown of complaints by subcategory, such as mobility and sensory disabilities, is provided.
- Visualization of complaints across U.S. states and by year.
### Conclusion
The analysis provides valuable insights into how airports in the U.S. are performing in terms of accessibility for individuals with disabilities. The findings can help inform decisions on where improvements are needed and which airports are doing well.
