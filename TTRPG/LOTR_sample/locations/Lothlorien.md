asset_family::TTRPG_asset
asset_type:: City
name::Lothlorien
race::
gender::
class::
world:: Middle Earth
location::
authority:: [[Galadriel]]
description:: An old powerful elven city
status:: Active
hit_points::
possessions::


This is where big shots elves live. Bosses are [[Galadriel]] and [[Elrond]]

```dataview
table name as "Name", authority as "Authority", description as "Description"
from "TTRPG/LOTR_sample"
where contains(location,[[Lothlorien]]) and contains(asset_type,"Shop")
```
```leaflet
id: leaflet-map
image: [[Pasted image 20221210154445.png]]
height: 500px
lat: 50
long: 50
minZoom: 1
maxZoom: 10
defaultZoom: 9
unit: meters
scale: 100
marker: default, 39.983334, -82.983330, [[Note]]
darkMode: False
```
