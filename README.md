# storm-heat-map
Repo to host a heat map of storm origin points.

# data source
This data is from the National Oceanic and Atmospheric Association (NOAA)'s [Storm Events Database](https://www.ncdc.noaa.gov/stormevents/ftp.jsp).

# data processing
I used mapshaper to process the data. Here are the commands I used to filter for relevant fields:

```
mapshaper storm-events.csv -filter-fields EVENT_TYPE,DAMAGE_PROPERTY,BEGIN_LAT,BEGIN_LON -0 format=csv storm-events.csv

```
And here are the commands I used to convert the csv into a geojson:

```
mapshaper storm-events.csv -points x=LON y=LAT -o format=geojson storm-events.geojson

```

I also used excel to help process the data when I couldn't find the right mapshaper commands. I had to delete all features for which was there was no property damage data and for which there were no lat/lon coordinates.

# mapping
I used the [Mapbox Heatmap Tutorial](https://www.mapbox.com/help/make-a-heatmap-with-mapbox-gl-js/) as the basis for this map. The heatmap tutorial is an intermediate tutorial that took me through the different options associated with heat maps. I manually chose the densities associated with the heat map colors and the radius of the circles underneath. I would like to create formal classifications for these in the future.
