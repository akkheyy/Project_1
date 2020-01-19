# Project_1
# CamMetro Bus Stops vs. Service Area Population Demographics Analysis

We began this project hoping to better understand the relationship between the poverty rate of an area, and the public transport quality of service (as measured by number of bus stops) to that area. We wanted to better understand how bus stops are distributed throughout the city and hypothesized that as the need is greater, or poverty rate is higher, in a given area, we would see a higher bus stop count in that area. We wanted to see what factors seemed to be taken into consideration in the configuration of our public bus route system.

We pulled down Population and Poverty Count from the Census API. This data came segmented by zip code. We then calculated the Poverty Rate by zip code, by dividing the total population by the count of those below the poverty line. 
The data pulled down from the CapMetro site gave us the latitude and longitude of each bus stop, but did not return zip codes! In order to attach zip codes, and thereby segment our data in a more meaningful way, we reverse geocoded the latitude and longitude of each bus stop to attach the zip codes to each bus stop.

We combined the data from each of these sources into one master dataset, from which we pulled the information necessary to construct the plots shown.

# CapMetro Bus Stops with Poverty Rate Contour Map
To construct the first plot, we interpolated the latitude & longitude data corresponding to each bus stop location. In order to work with these coordinates, we converted them to NumPy Arrays with Linspace. Linspace has essentially differentiated our numbers evenly and in such a way as to optimize the data for use within our contour map. The contour map requires that x, y and z are evenly spaced (the same length) as a pre-requisite in building the function. The ‘cubic’ here corresponds to Lat, Long & Poverty Rate which will serve as our x,y & z variables. These will be taken in as arguments for our contour plot. 
We then plot our contour map with parameters x, y and z. At given levels of 0-40%, as our poverty rate ranges from 0 to ~40% and stepping by scale 16. Where the contour is darker, we see higher incidents of those living below the poverty  line.
The scatter plot displays the location of each bus stop, while the line plot connects the latitude and longitude coordinates given, so as to display city of Austin boundaries. 
The lon_fake and lat_fake variables draw an arbitrary line around our bus stops, in order to set a parameter on the poverty data being fed to the contour map. Without this parameter, points on the map that are well outside of reach of the public transportation system will skew the contour map’s results toward these extrapolated points. These points don’t give us any insight or reflect accurate poverty rates! They are points automatically generated as a by-product of generating the contour map shown.
# Bus Stops vs. Austin Population
We can see with this next plot, the relationship between total population of a zip code and the number of bus stops per zip code. **We were surprised to find little correlation between the number of people living in a zip code’s area and the number of bus stops contained with that zip code**. One could conclude, that the City of Austin does not base much of it’s decisions on where to place bus stops on the population of a zip code alone.
# Bus Stops vs. Austin Poverty Rate
Next, we looked to investigate the relationship between poverty rate per zip code and the number of bus stops per zip code. **Did zip codes in greater need of public transportation see a higher instance of bus stops? In fact, it looks like there is correlation here perhaps indicating that quantity of bus stops in an area is adjusted to accommodate those most dependent on that service.**
# Number of Bus Commuters vs. Poverty Count
This graph could give insight to the preferred method of transportation of those living below the poverty line. **Are those living below the poverty line taking the bus?** Should the bus be the method most used, we would see the number of people riding the bus rise in those zip codes where the count of those people living below the poverty line is higher. 78741 is a zip code of note as this zip code sees a higher level of poverty and a higher use of bus stops as well.
# Number of Bus Commuters vs. Number of Bus Stops
This graph shows the actual volume of riders accommodated per stop, and gives a snapshot of how **crowded any given stop would be on a given day.** This can give valuable insight on the quality of service offered by our city buses by indicating how comfortable a ride users can expect on a day-to-day basis. Nobody likes an overly crowded bus! Were we to see a public bus system inundated with people, we may see use taper off as users turn to other methods of transportation such as bicycle or carpool.

# Further Considerations…
The first plot would perhaps be more useful with the zip code areas outlined. That way, we could more clearly understand the number of stops per zip code. Making this map interactive would be a fun feature as well!

One relationship that would be interesting to look into is that of the relationship between efficient transportation and unemployment rates. Transportation has been cited as the single most important factor to whether or not an individual is employed or not. If an individual cannot get to work, economic opportunity is limited. The relationship between unemployment and areas underserved by public buses is crucial. It follows that areas seeing a high incident of poverty rate that is also underserved by the public bus system, would perhaps see higher level of unemployment as well.

Another factor playing a role here would be those taking alternate forms of transport in order to get to work. How many travel by bike? Or carpool? Or walk? It’s important to understand these trends as we attempt to encourage more of the population to steer away from cars and toward greener, more sustainable methods of transport.

Furthermore, we would like to view the history of the CapMetro bus stops and poverty rate to see if there was a point in the past where the bus stops were not in locations of high poverty rate. We would also like to view how gentrification might currently be affecting the bus system, and if there are zip codes outside of the current service area that are seeing an increase in population and poverty rate and need access to the transit system. Are these areas underserved and how are those who can no longer afford to live in these areas being affected?

# Conclusion
Overall, it does appear that CapMetro plans the bus routes by need and looks to support those most in need by providing them with a robust system of public transport. 

