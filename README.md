# data-512-a1

## Goal of this project: 
This project is dedicated as a practice in best-practices and reproducibility of results in data science from data collection to analysis. 
This project is broken into a few steps. 

### Step 1: Data acquisition
In which we use wikipedia data gaathered from two APIs (a modern and legacy version) to gather traffic data on the english Wikipedia site from January 01, 2008 to the August 30, 2021 in both mobile and desktop formatts. Notice the modern API has mobile traffic in web and app seperately. we also put these data from 5 sources that we acquire into 5 seperate .json files.

### Step 2: Data processing
Next we begin preprocessing the data and manipulating it. We perform a couple of steps here including combining the mobile web traffic and mobile app traffic into one place which we take to be the whole 'mobile' traffic. We manipulate the timestamp variables in our data also to make it easier to graph and use in later steps. We remove uneccessary columns and keep only the ones that interest us (year, month, and counts of traffic among the different methods/APIs). We then create two new columns which represent 'all' traffic from both APIs by combining desktop and mobile traffic counts/views from both APIs seperately which gives us two new columns. After renaming these columns we output it as a csv file. 

### Step 3: Analysis
The final step of this is to visualize our data as a time series graph that matches a graph given by the instructor.  

## Data
My final data file has the following schema:  
Column        | Value
------------- | -------------
year          | YYYY
month         | MM
pagecount_all_views         | num_views (all traffic legacy API)
pagecount_desktop_views         | num_views (desktop traffic legacy API)
pagecount_mobile_views         | num_views (mobile traffic legacy API)
pageview_all_views         | num_views (all traffic modern API) 
pageview_desktop_views         | num_views (desktop traffic modern API)
pageview_mobile_views         | num_views (desktop traffic mobile API)

##Data Notes: 
The data in this project ranges from January 01, 2008 to August 30, 2021 

The following process was used to obtain the final data file:
- For data collected from the Pageviews API, combine the monthly values for mobile-app and mobile-web to create a total mobile traffic count for each month.
- For all data, separate the value of timestamp into four-digit year (YYYY) and two-digit month (MM) and discard values for day and hour (DDHH).
- Replace NaN values with 0 when creating the csv file

Additional Notes
- pagecount_all_views is the sum of pagecount_desktop_views and pagecount_mobile_views
- pagecount_desktop_views is from the legacy API
- pagecount_mobile_views is from the legacy API
- pageview_all_views is the sum of pageview_desktop_views and pageview_mobile_views
- pageview_desktop_views is from the modern API
- pageview_mobile_views is the sum of mobile_web and mobile_app values from the modern API.
- Remove the data from 08-2016 from the legacy API as it falls to 0 and messes up the graph
- The dates of the legacy mobile API and legacy desktop do not match so combine into pagecount_all_views only after merging all dektop and mobile views.
- Fill NaN values with 0 when creating the csv file use the unfilled data (containing NaN) for the visualization. 
- Replace pagecount_all_views NaN values with pagecount_desktop_views

## API

### API Notes
- Pageview API excludes spiders/crawlers
- Pagecounts API includes spiders/crawlers
- Filter by user on the modern API.
- Code to call API can be found [here](https://public.paws.wmcloud.org/User:Jtmorgan/data512_a1_example.ipynb) and is not mine.

### License and Terms of Use
Documentation for the legacy pagecounts API can be found [here](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)  
Documentation for the modern pageview API can be found [here](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews) 
The license and terms of use for the API can be found [here](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)

#### If there are any questions, feel free to contact me at sampereb@uw.edu
