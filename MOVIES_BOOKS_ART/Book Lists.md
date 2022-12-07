```dataview
table book_title as "Title", read_when as "Date of Reading"
where contains(type_book,null) = False and contains(read_when,null) = False
sort ASC
```

```dataview
table book_title as "Title", read_when as "Date of Reading"
where contains(type_book,"Book") and contains(read_when,null)
sort ASC
```
