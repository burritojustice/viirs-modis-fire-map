# viirs-modis-fire-map

Worldwide fire data (375m resolution) as detected by NASA/NOAA VIIRS (Suomi polar orbit) and MODIS (1km resolution), along with active fire boundaries from the USGS. 

Brighter colors indicate newer data, slider lets you tune the colors.

The CSVs are being pulled into a [HERE XYZ Space](https://here.xyz) every 20 minutes and cut into vector tiles on the fly so you can see global data from both VIIRS and MODIS soon after it is processed.

https://burritojustice.github.io/viirs-modis-fire-map/#lat=37.188&lng=-116.995&z=6.6750

Ventura fire from 2018:

![](viirs-modis-ventura.png)


## data

Note that VIIRS satellite passes are every ~12 hours (typically 1-3 AM & 1-3 PM for California), and the data usually available within 3 hours of that. MODIS data comes from two satellite, [Aqua and Terra](https://wiki.earthdata.nasa.gov/display/ESKB/Near+Real-Time+Data+Frequently+Asked+Questions). Terra (EOS AM) passes over the equator at approximately 10:30 am and 10:30 pm each day, Aqua (EOS PM) satellite passes over the equator at approximately 1:30 pm and 1:30 am. Sometimes there is line of sight so there is an extra set of data an hour before or after the main pass. (This is where the slider on the legend comes in handy -- if you set it for finer resolution, you can distinguish between all three passes.)

https://earthdata.nasa.gov/earth-observation-data/near-real-time/firms/active-fire-data

Fire names and boundaries are from GeoMAC/USGS -- these are updated daily, so don't expect to see it until a day after a fire is named.

https://rmgsc.cr.usgs.gov/outgoing/GeoMAC/current_year_fire_data/current_year_all_states/

@scuerda was kind enough to set up a geolambda on AWS that [converts the NOAA fire shapefiles to GeoJSON](https://github.com/scuerda/modis-viirs-conversion) every hour.

~Animation of data over time~: (sorry, broken right now)

~https://burritojustice.github.io/viirs-modis-fire-map/animation#lat=34.3966&lng=-119.2192&z=11.5542~


## map 

Default colors are divided into steps -- use the slider to change the "width"/ time range of the step in hours. White dots are the latest data, yellow the steps before that, orange the step before --  the darker the color, the older the data, using the [Viridis palette](https://github.com/politiken-journalism/scale-color-perceptual).

The date can be locked down as a global in the scene file. Primary source is defined on line 133, in the `viirs_7d:` url and `modis` layer.  This of course presumes you have data for that time.

_update of https://github.com/burritojustice/sonoma-napa-fire-map-viirs, now with a legend_

p.s. The Suomi NPP satellite is named after [Verner Suomi](https://en.wikipedia.org/wiki/Verner_E._Suomi), the guy who invented [spin-scan weather satellites](https://earthobservatory.nasa.gov/Features/Suomi/suomi_2.php).

https://twitter.com/UWSSEC/status/936254782158798854
