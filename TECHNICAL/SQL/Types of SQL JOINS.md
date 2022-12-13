article_type:: SQL
summary::
keywords::

Take 2 tables and join them in some way. 
![[Pasted image 20221213122617.png]]

# INNER JOIN
$A \cap B$
Select only records where join condition is met. Discard rest of rows.

Example
> SELECT a.name, b.salary
> FROM TABLE_A as a
> JOIN TABLE_B as b
> ON a.id = b.id


# LEFT (OUTER) JOIN


# FULL OUTER JOIN
