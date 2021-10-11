
# GDELT

I have created ETL design work.
ETL, which stands for extract, transform, and load, is the process data engineers use to extract data from different sources, transform the data into a usable and trusted resource, and load that data into the systems end-users can access and use downstream to solve business problems.
Architecture proposal has been created ended with an explanation.
Coding part with the testing folder.
To be scalable to process data streams in parallel.
Sources - GDELT PROJECT
   Basic use and new schema method                                                                       |
| ----------------- 
| import gdelt
gd= gdelt.gdelt()
events = gd.Search(['2017 May 23'],table='events',output='gpd',normcols=True,coverage=False)
new schema method
print(gd.schema('events')) | 

# GDELT Facts
GDELT 1.0 is a daily dataset.
1.0 only has 'events' and 'gkg' tables.
1.0 posts the previous day's data at 6 AM EST of the next day (i.e. Monday's data will be available 6 AM Tuesday EST)
GDELT 2.0 is updated every 15 minutes.
Some time intervals can have missing data; gdeltPyR provides a warning for missing data
2.0 has 'events','gkg', and 'mentions' tables.
2.0 has a distinction between native English and translated-to-English news
2.0 has more columns.


#New Features (0.1.10) as of Oct 2017
Added geodataframe output; can be easily converted into a shapefile or choropleth visualization.
Added continuous integration testing for Windows, OSX, and Linux (Ubuntu)
Normalized columns output; export data with SQL ready columns (no special characters, all lowercase)
Choosing between the native-English or translated-to-english datasets from GDELT v2.
Added schema method to query table info/column descriptions.


## Authors

- [@deekshanaarun](https://github.com/deekarun123/)

  
## Acknowledgements

 - [Reference of codes](https://www.gdeltproject.org/)
 - [More of content](https://www.gdeltproject.org/data.html)
 - [Analysis of dataset GDELT 3.0](https://blog.gdeltproject.org/gdelt-3-0-coming-soon/)

  ## Installation

|     gdeltPyR can be installed via pip                                                                       |
-------------------------------------- |
| pip install gdelt | 



## Basic Examples  GDELT 1.0 Queries
|     import gdelt                                                                       |
-------------------------------------- |
|Version 1 queries
gd1 = gdelt.gdelt(version=1)
pull single day, gkg table
results= gd1.Search('2016 Nov 01',table='gkg')
print(len(results))
 | 

## GDELT 2.0 Queries

|     import gdelt                                                                       |
-------------------------------------- |
|gd2 = gdelt.gdelt(version=2)
Single 15 minute interval pull, output to json format with mentions table
results = gd2.Search('2016 Nov 1',table='mentions',output='json')
print(len(results))
| 

## Output Options
## gdeltPyR can output results directly into several formats which include:

pandas dataframe,
csv,
json.
geopandas dataframe (as of version 0.1.10),
GeoJSON (coming soon version 0.1.11),
Shapefile (coming soon version 0.1.11),