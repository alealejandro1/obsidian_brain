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
