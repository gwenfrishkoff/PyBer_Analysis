# Exploratory Analysis and Visualization of Ride-Sharing Data (using Python, Pandas & Matplotlib)

## Project Overview
Our client is Omar, who works for Pyber, a python-based ride-sharing app company. Omar has asked us to conduct an exploratory analysis of ride-sharing data, using descriptive statistics and visualization of patterns and trends from rideshare data from January to early May of 2019 across 20 urban, rural, and suburban cities. He has requested the following deliverables:  
	<ol>
	<li> A summary DataFrame, i.e., a merged dataset (combining 2 source data files using Pandas);
	<li> A multiple-line chart of total fares for each city type that summarize patterns and trends for each the following:
		<ol>
		<li> The total number of rides for each city type;
		<li> The total number of drivers for each city type;
		<li> The sum of fares for each city type;
		<li> The average fare per ride for each city type; and 
		<li> The average fare per driver.
		</ol>
	<li> Three types of data visualizations:
		<ol>
		<li> Box-and-whisker plots to determine if there are outliers in the data;
		<li> A bubble chart that shows average fares versus the total number of rides; and
		<li> Pie charts that visualize percentage of total fares rides, and drivers for each city type (urban, rural, and suburban)
		</ol>
	</ol>

## Resources (Source Data & Analysis Software)
To accomplish these tasks, we used the following resources:
	<ol>
	<li> Data Source = (1) 'city_data.csv' and (2)'ride_data.csv'; and
	<li> Software = Python (v 3.9.7); Jupyter Notebook;
	</ol>

The first source data file (filename = 'city_data.csv') has the following structure:
	<ol>
	<li> It contains 121 rows (1st row = headers);
	<li> It contains 7 columns:
		<ol>
		<li> Column A contains strings
		<li> Column B contains integer data 
		<li> Column C contains strings
		</ol>
	<li> The headers (Keys) are:
		<ol>
		<li> "city" ('Amandaburgh': 'Williamsview', n=20)
		<li> "driver_count" (min=1, max =73)
		<li> "type" {'Urban', 'Rural', 'Suburban'}
		</ol>
	</ol>
 
The second source data file (filename = 'ride_data.csv') has the following structure:
	<ol>
	<li> It contains 2376 rows (1st row = headers);
	<li> It contains 3 columns:
		<ol>
		<li> Column A contains strings
		<li> Column B contains dates 
		<li> Column C contains numeric (floating-point) data 
		<li> Column D contains numeric IDs 
		</ol>
	<li> The headers (Keys) are:
		<ol>
		<li> "city" ('Amandaburgh': 'Williamsview', n=20)
		<li> "date" (custom format: date + timestamp)
		<li> "fare" (floating-point, .2F)
		<li> "ride_ID" (12- or 13-digits)
		</ol>
	</ol>

## Data Import, Inspection & Merging of DataFrames
We used Python (Pandas) to import the two source data (CSV) files and to inspect and merge the resulting DataFrames. For both datasets, we used _df.count() to verify that there are no missing (null) values. For the first source dataset ('city_data.csv'), we also performed the following checks:
	<ol>
	<li> We used the _df.dtypes() method to check that the 'driver_count' column contains integer data, which can be used for subsequent calculations;
	<li> We used the _df.unique() method to get a list of enumerated types ('Urban', 'Suburban', and 'Rural');
	<li> We used sum(_df["type"]) to get the number of data points for each of the three types(n=66 for 'Urban'; n=36 for 'Suburban'; n=18 for 'Rural');
	</ol>

For the second source dataset ('city_data.csv'), we used _df.dtypes() to verify that the data type for 'fare' is float (floating-point decimal), and the data type for and 'ride_id' is integer. After performing these checks, we used pd.merge() to combine the two datasets (merging on 'city').

## Methods for Exploratory Analysis: Descriptive Statistics (NumPy & SciPy)
We used NumPy (NP) np.mean() and np.median() functions, and the SciPy stats (STS) sts.mode() function, to compute summary statistics (script name = 'PyBer.ipynb'). When this code is run, it produces descriptive statistics, including the following:
		<ol>
		<li> The total number of rides for each city type;
		<li> The average fares for each city type; and 
		<li> The total number of drivers for each city type.
		</ol>

We created box-and-whisker plots to look for outliers (image file names = 'Fi2.png', 'Fig3.png', and 'Fig4.png'). 

## Methods for Data Visualization (Matplotlib)
We used Matplotlib to produce two additional types of data visualization:
	<ol>
	<li> A bubble chart --  shows average fare versus the total number of rides, with bubble size based on the average number of drivers for each city type: urban, suburban, and rural (image file name = 'Fig1.png'); and
	<li> A series of pie charts -- visualize the following data for each city type (image file names = 'Fig5.png', 'Fig6.png', & 'Fig7.png'):
		<ol>
		<li> Fig5.png shows the percentage of fares by city type;
		<li> Fig6.png shows the percentage of ride counts by city type; and 
		<li> Fig7.png shows the percentage of driver counts by city type;.
		</ol>
	</ol>

## Methods for Creating Multiple-Line Chart (Matplotlib)
We used an object-oriented interface method and the df.plot() method, together with the Matplotlib "fivethirtyeight" graph style, to create a multiple-line chart that shows changes in average fare per ride over time (from January through April 2019) for each city type. Results are saved to file (image file name = 'PyBer_fare_summary.png').

## Results
Exploratory analyses showed the following patterns and trends:
	<ol>
	<li> The number of rides tends to be lowest for rural cities (mean = 6.94) -- ~3.5 lower than in urban cities (mean = 24.62) and ~2.5 times lower than in suburban cities (n=17.36);
	<li> Average fares are highest for rural cities (mean = $34.62), slightly lower for suburban cities (mean = $30.97), and lowest for urban cities (mean = $24.53); and
	<li> The number of drivers tends to be lowest for rural cities (mean = 4.30) -- ~8.5 lower than in urban cities (mean = 36.68) and ~3 times lower than in suburban cities (n=13.71). 
	</ol>

Box-and-whisker plots (Fig2.png, Fig3.png, & Fig4.png) show the following results:
		<ol>
		<li> There is one outlier in the ride count data series (value = 39, from the city of West Angela);
		<li> There are no outliers in the average fares data series; and 
		<li> There are no outliers in the driver count data series.
		</ol>

Pie chart visualizations (Fig5.png, Fig6.png, & Fig7.png) suggest the following conclusions:
	<ol>
	<li> Urban city rides account for the largest percentage of fares (62.7%), followed by suburban cities (30.5%), and rural cities (6.8%);
	<li> Urban city rides account for the largest percentage of ride counts (68.4%), followed by suburban cities (26.3%), and rural cities (5.3%); and
	<li> Urban city rides are associated with the largest percentage of driver counts (80.9%), followed by suburban cities (16.5%), and rural cities (2.6%).
	</ol>

## Summary & Conclusions

The average fare for rides in the rural cities is highest: about $11 more per ride than in urban cites and and ~$5 more per ride than in suburban cities. This trend could be related to differences in supply and demand: the ratio of riders to drivers is lower in rural cities, so it is possible that drivers charge more in these areas.
