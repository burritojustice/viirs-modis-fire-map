# viirs-modis-fire-map

_update of https://github.com/burritojustice/sonoma-napa-fire-map-viirs, now with a legend_

![](viirs-modis-ventura.png)

## data

US (Conterminous and Hawaii) Fire data (375m resolution) via NASA/NOAA VIIRS (Suomi polar orbit) and MODIS (1km resolution), along with active fire boundaries from the USGS.

@scuerda was kind enough to set up a geolambda on AWS that [converts the NASA shapefile to GeoJSON](https://github.com/scuerda/modis-viirs-conversion) every hour! 

Note that VIIRS satellite passes are every ~12 hours (typically 1-3 AM & 1-3 PM for California), and the data usually available within 3 hours of that. MODIS data comes from two satellite, [Aqua and Terra](https://wiki.earthdata.nasa.gov/display/ESKB/Near+Real-Time+Data+Frequently+Asked+Questions). Terra (EOS AM) passes over the equator at approximately 10:30 am and 10:30 pm each day, Aqua (EOS PM) satellite passes over the equator at approximately 1:30 pm and 1:30 am. Sometimes there is line of sight so there is an extra set of data an hour before or after the main pass. (This is where the slider on the legend comes in handy -- if you set it for finer resolution, you can distinguish between all three passes.)

https://earthdata.nasa.gov/earth-observation-data/near-real-time/firms/active-fire-data

This displays the 7 day file for the contiguous US -- you could easily load other areas of the world or the global files, see below.

Fire names are from GeoMAC/USGS:

https://rmgsc.cr.usgs.gov/outgoing/GeoMAC/current_year_fire_data/current_year_all_states/

## map 

scene file:

https://mapzen.com/tangram/play/?api=22/1271#11.4875/34.3321/-119.1843

Default colors are divided into 12 hour steps. White dots are the latest data, yellow 12 hours before that, orange the day before, red 12 hours before that -- the darker the color, the older the data, using the [Viridian palette](https://github.com/politiken-journalism/scale-color-perceptual).

The `Time window` buttons change the time range of each color. 

The date can be locked down as a global. Primary source is defined on line 133, in the `viirs_7d:` url. 



