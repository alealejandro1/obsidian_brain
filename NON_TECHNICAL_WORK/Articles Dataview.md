
```dataview
table article_title as "Title", year_posted as "Year Posted", my_rating as "Rating"
where contains(article_title,null) = False
sort my_rating DESC
```


