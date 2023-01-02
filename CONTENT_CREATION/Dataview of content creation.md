# Un-published
```dataview
table tagline as "Tag Line"
from "CONTENT_CREATION"
where contains(published,False)
```
# Published
```dataview
table tagline as "Tag Line"
from "CONTENT_CREATION"
where contains(published,True)
```