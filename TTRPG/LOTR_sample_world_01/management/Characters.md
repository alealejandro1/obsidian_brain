
# Alive Characters
```dataview
table name as "Name", notetype as "Character Type"
from "TTRPG/LOTR_sample_world_01"
where contains(notetype,"#PC") or contains(notetype,"#NPC") and contains(status,"Alive")
SORT file.notetype ASC
```

# Dead Characters
```dataview
table name as "Name", notetype as "Character Type"
where contains(notetype,"NPC") or contains(notetype,"PC")
and contains(status,"Dead")
sort ASC
```
