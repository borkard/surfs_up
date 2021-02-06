# Surfs Up Weather Analysis

## Overview
SQLite, SQLAlchemy, Pandas, and Python were used to conduct a weather analysis to determine whether a year-round surf shop and ice cream business will be sustainable in Oahu, HI.
Temperature data was pulled for the months of June and December and summary statistics were retrieved to compare.

## Results
Images of the summary statistics for temperatures in Oahu, Hawaii for June and December are below, followed by some observations. 

**June Temperature Summary**
![june_temps.PNG](https://github.com/borkard/surfs_up/blob/main/june_temps.PNG)

**December Temperature Summary**
![december_temps.PNG](https://github.com/borkard/surfs_up/blob/main/december_temps.PNG)

* The maximum temperature for both December and June are fairly close (83 and 85 respectively), however, the minimum temperatures for December and June differ by 8 degrees.
* The mean temperature for both December and June (71 and 75 respectively) are also fairly close.
* The range of temperatures for December is 27 degrees compared to 21 degrees for June temperatures.


## Summary
Based on the results, with a similar average temperature for the months of June and December, as well as a similar maximum temperature and range, it would make sense to have the surf and ice cream shop open year-round. Additional queries could be performed to retrieve and describe the precipitation data to understand the rainfall for the area in these months to ensure green land and sunny days to surf. Some code of how this precipitation data could be retrieved and summarized are below:

**June Precipitation**
*Write a query that filters the Measurement table to retrieve the precipitation for the month of June.*
j_prcp = []
j_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==6)

*Convert the June precipitation into a list.*
june_prcp = j_prcp.all()

*Create a DataFrame from the list of precipitation for the month of June.*
june_prcp_df = pd.DataFrame(june_prcp, columns=["date", "June Precipitation"])
display(june_prcp_df)

*Calculate and print out the summary statistics for the June precipitation DataFrame.*
june_prcp_df.describe()

![june_prcp.PNG](https://github.com/borkard/surfs_up/blob/main/june_prcp.PNG)

**December Precipitation**
*Write a query that filters the Measurement table to retrieve the precipitation for the month of December.*
d_prcp = []
d_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==12)

*Convert the December precipitation into a list.*
dec_prcp = d_prcp.all()

*Create a DataFrame from the list of precipitation for the month of December.*
dec_prcp_df = pd.DataFrame(dec_prcp, columns=["date", "December Precipitation"])
display(dec_prcp_df)

*Calculate and print out the summary statistics for the December precipitation DataFrame.*
dec_prcp_df.describe()

![december_prcp.PNG](https://github.com/borkard/surfs_up/blob/main/december_prcp.PNG)
