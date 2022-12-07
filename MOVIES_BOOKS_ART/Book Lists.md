```dataview
table book_title as "Title", read_when as "Date of Reading"
where contains(type_book,"Book")
```


type_book:: Book
book_title::Close to the machine
read_when::2020
good_about_book:: Snapshot of late 90s database system integrators, Mixes complex life with growing out of technical role into manager path
bad_about_book::Whole sub-plot involving her family wasn't very interesting or relevant

```dataview
table name as "Name", notetype as "Character Type"
where contains(notetype,"NPC") or contains(notetype,"PC")
and contains(status,"Dead")
sort ASC