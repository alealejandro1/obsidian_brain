#SummaryTable 
```dataview
table title as "City", country as "Country", keywords as "Keywords"
from "TOURISM"
where contains(note_type,"Tourism")
```

```leaflet
id: leaflet-cities-visited
image: 
height: 800px
lat: 50
long: 10
minZoom: 1
maxZoom: 10
defaultZoom: 1
unit: meters
scale: 1
marker: default
darkMode: False
```

