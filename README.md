# National-scale spatiotemporal variation in driver behaviour

'Understanding the complexities of human behaviour and movement are essential for advancements in various contexts, ranging from emergency services (Liu et al., 2022) to official statistics (Marchetti et al., 2016; Pappalardo et al., 2016). Traditional data collection methods, such as surveys, have been limited regarding collection frequency (Punzo et al., 2011). Though the use of mobile phones has been an invaluable source of data for studying movement behaviour, it does not offer the level of granularity provided by connected car data (Chen et al., 2019)' (Karikari et al., 2023)

In this project, we analyse GPS data from over 1 million journeys by 50,000 connected cars across the UK.


# Route Analysis Framework

We explored routing behaviour through the generation of descriptive statistics. No preprocessing was required as raw data is highly accurate. Scikit mobility, a Python library for human mobility analysis, was used to generate travel distance and stop time metrics (Pappalardo et al., 2019). The following statistics have been computed:

**Travel Distance: Revealing the Length of Journeys** - The travel distance metric (L) captures the length of a journey. We computed it by summing the distances between consecutive time-ordered GPS points, where the number of points is denoted by 'n.' The equation (1) represents the calculation:

L = Σ𝑑𝑖𝑠𝑡(𝑟𝑗− 1,𝑛𝑗=2 𝑟𝑗) (1)

**Travel Time** – This statistic measures the duration of a journey (D). This is computed in Equation 2 as the difference between the timestamps of the first (t1) and last (tn) GPS recordings for a journey.

𝐷 = 𝑡𝑛 − 𝑡1 (2)

**Stop Time** - This statistic measures the total stop time within a journey. GPS points which were stationary (i.e. within a spatial radius of 200 m) for a minute or more were identified as stops (see Table 1 of Hariharan and Toyama, 2004 for a definition). Places of interest, identified by long stop times, are considered pull factors in analysing route choice. Shorter stops resultant from traffic are also identified.

**Number of Turns** - The number of turns along a journey is determined by the bearing change between two consecutive trajectory points. Bearing changes greater than 50° are considered as turns (Douglas and Peucker, 1973). This statistic helps to understand the patterns regarding routes taken, i.e. are people more likely to go along a route without many turns or not.

**Cumulative Angular Deviation** – The CAD measures the angularity of the trajectory. This is defined in Equation 3 as the sum of the absolute differences in bearing angle between consecutive time-ordered points of the journey, where n is the number of points, and θj-1 and θj are bearings of consecutive points.

CAD = Σ|𝜃𝑗−1−𝜃𝑗|𝑛𝑗=2 (3)

**Sinuosity** – The sinuosity S measures the trajectory efficiency, compared to a straight line. It is the ratio of the route length L to the straight-line distance between origin (r1) and destination (rn), as defined in Equation 4.

𝑆 = 𝐿𝑑𝑖𝑠𝑡(𝑟1, 𝑟𝑛) (4)

# Code
The uploaded version of the code used to generate the output is not the final version and may contain errors and incomplete steps. This has been uploaded to display my coding ability.

🏋 Generating Statistical Measures.ipynb - Once I had the data, I first tried to visualise it. I used datashader to visualise all 400 million points and used osmnx to visualise individual journeys (Not in code). 

This notebook shows the code used to generate statistical measures used to explore routing behaviour.

🏊‍♂️ Statistical Analysis, Results & Visualisation.ipynb - This notebook contain exploratory data analysis of statistical measures over time. It also shows how variables are related to each other. 

🌍 Geographic Variation.ipynb - This notebook show statistical variation over space. It also contains the geographic variation of clusters identified.  

🥤 Clustering.ipynb - Contains code used to identify types of journeys made.
