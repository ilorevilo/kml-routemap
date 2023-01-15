# Simplify and merge individual gpx tracks into a single styled kml file

Gpx tracks recorded from bicycle tours are generally quite large, containing too detailed route information or details which are not needed for just displaying the route. Furthermore uploading individual tracks to google mymaps and styling them individually is quite tiresome.
[kml-routemap.ipynb](kml-routemap.ipynb) demonstrates the automated kml map generation from recorded tours, including a defined layer styling:
- routes are simplified for file size reduction
- each route is coloured in alternating colours such that individual segments can be distinguished from a connected route (e.g. routes on a onnected 10 day route are coloured red for even days, blue for uneven days)
- for each track/ segment additional metadata is added, describing route length and accumulated elevation (styled with emojis, e.g. 🚴🏽‍♀️🚴🏼‍♂️)

## input
- place all gpx tracks into folder
- name files according to desired sorting order, here I used `TIMESTAMP_xx Routename.gpx` where `xx` is used for the track color
  - routes on the same day which consist of 2 segments (e.g. recorded before/ after a ferry ride) but should share the same colour should be named with an underscore, e.g. `xx = 31_1` or `31_2`
  - adjust the script if you have a different naming scheme/ want a different styling

## output
`merged_kml.kml` can be directly uploaded to google mymaps. Individual styles are applied according to the route index and the metadata is displayed when clicking on the route segment.
Check out a map styled with this script [here](https://www.google.com/maps/d/embed?mid=1VXg4p-IgKw4mUo2xqkbYZKyJgb24VMo&ehbc=2E312F).

## to improve
each time the script is called, all routes are processed. To speed things up it is conceivable to:
- store shrinked gpx-files temporarily
- or append new gpx-files to kml