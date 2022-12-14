article_type:: SQL
summary:: Inner query is independent of outer query in Nested, whereas both are dependent on Correlated Query.
keywords:: Correlated Query, Nested Query, Inner Query, Outer Query

General approach is this:
OUTER QUERY (INNER QUERY)

# Nested Query
There is an Outer Query and an Inner query. Inner query runs first and is independent of outer query.


> SELECT * FROM CUSTOMERS
> WHERE CustomerID in (SELECT CustomerID FROM ORDERS);

# Correlated Query
There are 2 queries that are dependent on each other. For everytime the outer query returns a row, the inner query must run again.

>SELECT e.name, e.dep_ID
>FROM employee as e
>WHERE e.dep_ID = (SELECT id from department WHERE id = e.dep_ID)