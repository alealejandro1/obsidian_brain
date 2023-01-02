#SummaryTable 
```dataview
table country as "Country", last_visited as "Last Visited", keywords as "Keywords"
from "TOURISM"
where contains(note_type,"Tourism")
sort last_visited ASC
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

