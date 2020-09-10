# Snowflake Usage and Metadata Dashboard:

This Qlik Sense app combines data from multiple Snowflake tables to
create an understanding of three key areas.

\- Cost / Usage Analysis: There are two versions of this focused on
pay-as-you go models or Enterprise credit purchases.

\- Auditing / Security: Show who is logging in from where (GeoAnalytics)
and metrics associated with Security and Connectivity.

\- Performance & Optimization: Who is running queries, where are their
issues - how does this relate to cost and usage?

Instructions and descriptions are below. Here is a video showing the dashboard in action: https://www.youtube.com/watch?v=4cNBdX9hufs

### If you are new to Qlik: Click here to get started -- https://help.qlik.com/en-US/onboarding

The app can be downloaded
from the root GitHub directory of this project.  There are two versions of the dashboard, as simplified version to get started quickly, and a more complex version that supports Qlik Server Side Extensions. For more information and how to use Server Side Extensions for Qlik Sense, visit here:

https://github.com/nabeel-oz/qlik-py-tools

Upload to your Qlik Sense server, Qlik cloud (when the Snowflake driver
is enabled), or Qlik Sense Desktop. Follow the instructions in the app
to add your Snowflake credentials and update the GeoAnalytics connection
or modify to use a public IP lookup service. 

A demo version using the
Qlik Partner Engineering account can be accessed
[**here**](https://pe.qlik.com/sense/app/100104c2-3917-4f44-b1b3-677c92846d60/overview):

![](./media/qlik-snowflake-architecture.png)
***About Qlik and the App:***

Qlik is the only major analytics vendor with an entire data integration and
management suite powering the data from raw to ready across an
enterprise. This application specifically uses the Qlik Sense component
to visualize the usage and cost data about a Snowflake instance sourced
from internal tracking tables. Qlik Sense is unique in the analytics
space as it is three tools in a single product encompassing an ELT
engine, a high speed memory cache, and world class data
visualization and analytics.

![](./media/image2.jpeg)

**Data Model:**

The data is collected from a series of methods and combined together in
Qlik's in-memory associative engine. Qlik is unique in that unlike other
BI/Visualization tools it can handle multi-grain fact scenarios with
data at different levels of aggregation and granularity. For this
application, we are combining metadata from databases, tables, and
columns with query performance data, login information, storage costs,
and usage costs. We also perform dynamic IP lookups to get geospatial
information about user IP locations.

**Data Load Script:**

![](./media/image3.jpeg)

The data is extracted using Qlik load script. The load scripts are how
Qlik requests the data from the source tables, sql functions, and
geo-lookups. The model for this application has been broken into logical
grouping of similar data by using tabs to help simplify understanding of
the data imported. In order to map this application to your instance of
Snowflake, you will need to create your own data connection to
Snowflake. With the September 2019 release of Qlik Sense Enterprise,
there is a built-in connector. Older versions of Qlik Sense will require
a download of the ODBC driver from the Snowflake website.

![A screenshot of a cell phone Description automatically
generated](./media/image4.jpeg)![A screenshot of a cell phone Description
automatically
generated](./media/image5.jpeg)

The other element in the load script in the Qlik GeoAnalytics IP lookup.    
Please note this is a licensed add-on to Qlik Sense and will not work without a license.  
You can contact your Qlik representative for an evaluation license.    

Alternatively, you could use the external IP via api REST lookup solution as described in the load script…

This section of the script takes the unique IP's from the Login History
in-memory table and passes them to the GeoAnalytics engine and returns
City, State, Country, and Lat/Long values for each IP.

## About the Dashboard

**Table of Contents:**

This is the basic introduction to the layout and structure of the app.   You can use the buttons under Table of Contents to navigate the app.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image6.jpeg)

**Usage Cost:**

This dashboard shows costs and usage associated with Snowflake usage.
Note how Qlik's engine has mapped estimated costs down to a user level.
This is a mixed grain fact situation so costs are dynamically allocated
and may not be exact -- but do give a general estimate on usage/cost
comparison. Users can alter their cost per credit and storage costs
based on their unique pricing models that may be applicable.

> ![A screenshot of a social media post Description automatically
> generated](./media/image7.jpeg)

**Enterprise Credit Usage:**

This dashboard is based on consumption of pre-purchased credits vs
usage. The Vizlib chart projects when purchased credits will run out.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image8.jpeg)

**Auditing / Security:**

This dashboard uses the GeoAnalytics IPlookup feature to display where
users are logging in from around the globe. Also allows for
investigation how users are accessing the system, version of drivers
used, and when/how often users are accessing the system.

> ![A close up of a map Description automatically
> generated](./media/image9.jpeg)

**Performance / Optimization:**

This dashboard can be used to understand query performance, usage
hotspots, query volumes vs runtime, errors, and dive deep into query
details.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.jpeg)

**Storytelling:**

Using the story mode provides an example of how data can be used to
answer questions and present them in a instructional method. Story mode can be accessed using the **Story** tab on the top of the screen.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image11.jpeg)
