#SummaryTable 
# Non-Fiction Books I've read

```dataview
table my_score as "Rating", keywords as "Key Words"
where contains(type_book,"Non-Fiction") and contains(read_when,null) = False
and contains(asset_type,"Book")
sort read_when DESC
``` 


# Fiction Books I've read

```dataview
table title as "Title", read_when as "Date of Reading", my_score as "Rating"
where contains(type_book,"Non-Fiction")=False and contains(read_when,null) = False
and contains(asset_type,"Book")
sort read_when DESC
```


# Book I haven't read yet
```dataview
table title as "Title" 
where contains(type_book,null) = False and contains(read_when,null)
sort ASC
```


