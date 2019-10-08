**Snowflake Usage and Metadata Dashboard:**

This Qlik Sense app combines data from multiple Snowflake tables to
create an understanding of three key areas.

\- Cost / Usage Analysis: There are two versions of this focused on
pay-as-you go models or Enterprise credit purchases.

\- Auditing / Security: Show who is logging in from where (GeoAnalytics)
and metrics associated with Security and Connectivity.

\- Performance & Optimization: Who is running queries, where are their
issues - how does this relate to cost and usage?

Instructions and descriptions are below. The app can be downloaded
**[here]{.underline}**:

Upload to your Qlik Sense server, Qlik cloud (when the Snowflake driver
is enabled), or Qlik Sense Desktop. Follow the instructions in the app
to add your Snowflake credentials and update the GeoAnalytics connection
or modify to use a public IP lookup service. A demo version using the
Qlik Partner Engineering account can be accessed
[**here**](https://pe.qlik.com/sense/app/c9d2fe49-1afa-4982-a3b8-95d3ca7e63b5):

The other elements used in the app are Vizlib dashboards. Learn more at
<http://vizlib.com>.

![](./media/image1.png){width="4.289583333333334in"
height="2.5833333333333335in"}[About the Qlik and the App]{.underline}:

Qlik is the only major analytics vendor with an entire data movement and
management suite powering the data from raw to ready across an
enterprise. This application specifically uses the Qlik Sense component
to visualize the usage and cost data about a Snowflake instance sourced
from internal tracking tables. Qlik Sense is unique in the analytics
space as it is three tools in a single product encompassing an ELT
engine, an in-memory columnar database, and world class data
visualization and analytics.

![](./media/image2.jpeg){width="2.4097222222222223in"
height="2.3953062117235344in"}[Data Model]{.underline}:

The data is collected from a series of methods and combined together in
Qlik's in-memory associative engine. Qlik is unique in that unlike other
BI/Visualization tools it can handle multi-grain fact scenarios with
data at different levels of aggregation and granularity. For this
application, we are combining metadata from databases, tables, and
columns with query performance data, login information, storage costs,
and usage costs. We also perform dynamic IP lookups to get geospatial
information about user IP locations.

Data Load Script:

![](./media/image3.jpeg){width="4.916666666666667in"
height="1.9130872703412074in"}

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
generated](./media/image4.jpeg){width="3.5625in"
height="2.0198917322834644in"}![A screenshot of a cell phone Description
automatically
generated](./media/image5.jpeg){width="2.7222222222222223in"
height="1.9573239282589676in"}

The other element in the load script in the Qlik GeoAnalytics IP lookup.
This section of the script takes the unique IP's from the Login History
in-memory table and passes them to the GeoAnalytics engine and returns
City, State, Country, and Lat/Long values for each IP.

**About the Dashboard**

Table of Contents:

This is the basic introduction to the layout and structure of the app.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image6.jpeg){width="4.569444444444445in"
> height="2.0538090551181103in"}

Usage Cost:

This dashboard shows costs and usage associated with Snowflake usage.
Note how Qlik's engine has mapped estimated costs down to a user level.
This is a mixed grain fact situation so costs are dynamically allocated
and may not be exact -- but do give a general estimate on usage/cost
comparison. Users can alter their cost per credit and storage costs
based on their unique pricing models that may be applicable.

> ![A screenshot of a social media post Description automatically
> generated](./media/image7.jpeg){width="4.583333333333333in"
> height="2.155538057742782in"}

Enterprise Credit Usage:

This dashboard is based on consumption of pre-purchased credits vs
usage. The Vizlib chart projects when purchased credits will run out.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image8.jpeg){width="4.583333333333333in"
> height="2.0639687226596677in"}

Auditing / Security:

This dashboard uses the GeoAnalytics IPlookup feature to display where
users are logging in from around the globe. Also allows for
investigation how users are accessing the system, version of drivers
used, and when/how often users are accessing the system.

> ![A close up of a map Description automatically
> generated](./media/image9.jpeg){width="4.583333333333333in"
> height="2.0585826771653544in"}

Performance / Optimization:

This dashboard can be used to understand query performance, usage
hotspots, query volumes vs runtime, errors, and dive deep into query
details.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.jpeg){width="4.597222222222222in"
> height="2.0751356080489938in"}

Storytelling:

Using the story mode provides an example of how data can be used to
answer questions and present them in a instructional method.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image11.jpeg){width="4.736111111111111in"
> height="2.674688320209974in"}
