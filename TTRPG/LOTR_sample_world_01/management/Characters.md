```dataview
table name as "Name", notetype as "Character Type"
from "TTRPG/LOTR_sample_world_01"
where contains(notetype,"#PC") or contains(notetype,"#NPC")
SORT file.notetype ASC
```
