# viirs-modis-fire-map

Conterminous US and Hawaii fire data (375m resolution) as detected by NASA/NOAA VIIRS (Suomi polar orbit) and MODIS (1km resolution), along with active fire boundaries from the USGS. Brighter colors indicate newer data, slider lets you tune the colors.
http://geojson.tools/tangram/play/?#9.8580/19.2649/-874.9753%20
~https://burritojustice.github.io/viirs-modis-fire-map/#lat=34.3966&lng=-119.2192&z=11.5542~ _while I work out dependencies..._

Animation of data over time:

~https://burritojustice.github.io/viirs-modis-fire-map/animation#lat=34.3966&lng=-119.2192&z=11.5542~

![](viirs-modis-ventura.png)

## data

@scuerda was kind enough to set up a geolambda on AWS that [converts the NASA shapefile to GeoJSON](https://github.com/scuerda/modis-viirs-conversion) every hour! 

Note that VIIRS satellite passes are every ~12 hours (typically 1-3 AM & 1-3 PM for California), and the data usually available within 3 hours of that. MODIS data comes from two satellite, [Aqua and Terra](https://wiki.earthdata.nasa.gov/display/ESKB/Near+Real-Time+Data+Frequently+Asked+Questions). Terra (EOS AM) passes over the equator at approximately 10:30 am and 10:30 pm each day, Aqua (EOS PM) satellite passes over the equator at approximately 1:30 pm and 1:30 am. Sometimes there is line of sight so there is an extra set of data an hour before or after the main pass. (This is where the slider on the legend comes in handy -- if you set it for finer resolution, you can distinguish between all three passes.)

https://earthdata.nasa.gov/earth-observation-data/near-real-time/firms/active-fire-data

This displays the 7 day file for the contiguous US -- you could easily load other areas of the world or the global files, see below.

Fire names and boundaries are from GeoMAC/USGS -- these are updated daily, so don't expect to see it until a day after a fire is named.

https://rmgsc.cr.usgs.gov/outgoing/GeoMAC/current_year_fire_data/current_year_all_states/

## map 

scene file:

https://mapzen.com/tangram/play/?api=22/1271#11.4875/34.3321/-119.1843

Default colors are divided into steps -- use the slider to change the "width"/ time range of the step in hours. White dots are the latest data, yellow the steps before that, orange the step before --  the darker the color, the older the data, using the [Viridian palette](https://github.com/politiken-journalism/scale-color-perceptual).

The date can be locked down as a global in the scene file. Primary source is defined on line 133, in the `viirs_7d:` url and `modis` layer. 

_update of https://github.com/burritojustice/sonoma-napa-fire-map-viirs, now with a legend_

p.s. The Suomi NPP satellite is named after [Verner Suomi](https://en.wikipedia.org/wiki/Verner_E._Suomi), the guy who invented [spin-scan weather satellites](https://earthobservatory.nasa.gov/Features/Suomi/suomi_2.php).

https://twitter.com/UWSSEC/status/936254782158798854
