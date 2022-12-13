article_type:: SQL
summary:: Joining two tables based on their similarities
keywords:: INNER JOIN, LEFT JOIN, FULL OUTER JOIN, CROSS JOIN

Take 2 tables and join them in some way. 
![[Pasted image 20221213122617.png]]
![[Pasted image 20221213123934.png]]


# INNER JOIN
$A \cap B$
Select only records where join condition is met. Discard rest of rows.

Example
> SELECT a.name, b.salary
> FROM TABLE_A as a
> JOIN TABLE_B as b
> ON a.id = b.id


# LEFT (OUTER) JOIN
$A \cup (A \cap B) = A$
Select all records from A, along with records from B where the condition is met. 

Note: Left Join might show you some rows that don't exist on table B, that exist only in A.

>SELECT a.name, b.salary
>FROM TABLE_A as a
>LEFT JOIN TABLE_B as b
>ON a.id = b.id


# FULL OUTER JOIN
$A \cup B$
This JOIN is not supported on [[MySQL]]

SELECT all records from A&B whatever match there is (if any).

> SELECT a.name, b.salary
> FROM TABLE_A as a
> LEFT JOIN TABLE B as b
> ON a.id=b.id
> UNION ALL   
> SELECT a.name, b.salary
> FROM TABLE_A as a
> RIGHT JOIN TABLE_B as b
> ON a.id = b.id
> WHERE TABLE_A.id IS NULL

Note: Union ALL will include duplicates, so we must add a WHERE statement to consider rows that were not present in the first join by considering TABLE_A.id IS NULL


# CROSS JOIN
$A \times B$
Cartesian Product of rows. 
Does not have a "ON" or "USING" clause to join tables.

> SELECT a.name, b.salary
> FROM TABLE_A as a
> CROSS JOIN TABLE_B as b

