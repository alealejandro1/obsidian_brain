
# Alive Characters

```dataview
table name as "Name", asset_type as "Character Type", race as "Race"
from "TTRPG/LOTR_sample"
where contains(asset_type,"PC") or contains(asset_type,"NPC") and contains(status,"Alive")
SORT file.name ASC
```
^LOTRAliveCharacters

# Dead Characters
```dataview
table name as "Name", asset_type as "Character Type", race as "Race"
from "TTRPG/LOTR_sample"
where contains(asset_type,"PC") or contains(asset_type,"NPC") and contains(status,"Dead")
SORT file.name ASC
```


# Random Character Dice Roll
`dice: [[Characters#^LOTRAliveCharacters]]`
