```dataview
table title as "City", country as "Country", keywords as "Keywords"
from "TOURISM"
where contains(note_type,"Tourism")
```

```leaflet
id: leaflet-map
image: 
height: 800px
lat: 50
long: 50
minZoom: 1
maxZoom: 10
defaultZoom: 2
unit: meters
scale: 1
marker: default
darkMode: False
```

