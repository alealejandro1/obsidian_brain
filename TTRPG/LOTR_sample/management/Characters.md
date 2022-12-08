
# Alive Characters

```dataview
table name as "Name", notetype as "Character Type"
from "TTRPG/LOTR_sample"
where contains(notetype,"#PC") or contains(notetype,"#NPC") and contains(status,"Alive")
SORT file.notetype ASC
```
^LOTRAliveCharacters

# Dead Characters
```dataview
table name as "Name", notetype as "Character Type"
where contains(notetype,"NPC") or contains(notetype,"PC")
and contains(status,"Dead")
sort ASC
```


# Random Character Dice Roll
`dice: [[Characters#^LOTRAliveCharacters]]`
