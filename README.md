# National-scale spatiotemporal variation in driver behaviour

'Understanding the complexities of human behaviour and movement are essential for advancements in various contexts, ranging from emergency services (Liu et al., 2022) to official statistics (Marchetti et al., 2016; Pappalardo et al., 2016). Traditional data collection methods, such as surveys, have been limited regarding collection frequency (Punzo et al., 2011). Though the use of mobile phones has been an invaluable source of data for studying movement behaviour, it does not offer the level of granularity provided by connected car data (Chen et al., 2019)' (Karikari et al., 2023)

In this project, we analyse GPS data from over 1 million journeys by 50,000 connected cars across the UK.


# Route Analysis Framework

We explored routing behaviour through the generation of descriptive statistics. No preprocessing was required as raw data is highly accurate. Scikit mobility, a Python library for human mobility analysis, was used to generate travel distance and stop time metrics (Pappalardo et al., 2019). The following statistics have been computed:

**Travel Distance: Revealing the Length of Journeys** - The travel distance metric (L) captures the length of a journey. We computed it by summing the distances between consecutive time-ordered GPS points, where the number of points is denoted by 'n.' The equation (1) represents the calculation:

L = Σ𝑑𝑖𝑠𝑡(𝑟𝑗− 1,𝑛𝑗=2 𝑟𝑗) (1)

**Travel Time: Measuring the Duration of Journeys** – The travel time metric (D) quantifies the duration of a journey. It was computed by taking the difference between the timestamps of the first (t1) and last (tn) GPS recordings for a given journey. The equation (2) shows this calculation:

𝐷 = 𝑡𝑛 − 𝑡1 (2)

**Stop Time: Identifying Stops and Analyzing Pull Factors** - The stop time metric helps us understand the total amount of time spent at stationary GPS points within a journey. Stops were identified when the car remained within a spatial radius of 200 meters for a minute or longer. These stops can indicate places of interest, acting as pull factors in analyzing route choice. Additionally, shorter stops resulting from traffic conditions were also identified and accounted for.

**Number of Turns: Shedding Light on Route Patterns** - The number of turns along a journey provides insights into the patterns and preferences regarding the routes taken. We determined the number of turns by analyzing the bearing change between consecutive trajectory points. Turns were considered when the bearing change exceeded 50°, as defined by Douglas and Peucker (1973).

**Cumulative Angular Deviation: Measuring Trajectory Angularity** – The cumulative angular deviation (CAD) metric quantifies the angularity of a trajectory. It is computed by summing the absolute differences in bearing angles between consecutive time-ordered points of a journey. The equation (3) shows this calculation:

CAD = Σ|𝜃𝑗−1−𝜃𝑗|𝑛𝑗=2 (3)

**Sinuosity: Evaluating Route Efficiency** – The sinuosity S measures the trajectory efficiency, compared to a straight line. It is the ratio of the observed route length L to the straight-line distance between origin (r1) and destination (rn) points, as defined in Equation 4.

𝑆 = 𝐿𝑑𝑖𝑠𝑡(𝑟1, 𝑟𝑛) (4)

# Code
To extract meaningful insights, we developed comprehensive code using **Python**.

The uploaded version of the code used to generate the output is not the final version and may contain errors and incomplete steps. This has been uploaded to display my coding ability.

🏋 **Generating Statistical Measures.ipynb** - Once I had the data, I first tried to visualise it. I used datashader to visualise all 400 million points and used osmnx to visualise individual journeys (Not in code). 
This notebook shows the code used to generate statistical measures used to explore routing behaviour.

🏊‍♂️ **Statistical Analysis, Results & Visualisation.ipynb** - This notebook contains the statistical analysis, explored results, and employed data visualization techniques. It also shows the relationships among variables and provides exploratory data analysis of the statistical measures over time

🌍 **Geographic Variation.ipynb** - This notebook shows the spatial distribution of statistical variations and includes geographic variation of identified clusters. 

🥤 **Clustering.ipynb** - This notebook identifies distinct types of journeys made by drivers, revealing valuable insights into their behavior patterns.

# Timeline - 6 month Project 
Work was done over a period of **4 months** as data was made roughly available 2 months after the start of the project. 
