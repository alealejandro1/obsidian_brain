article_type:: [[SQL]]
summary:: A view is a virtual table, it is the result of a SQL query. You can run queries on views as if they are tables. 
keywords:: Virtual Table, Security, Reusability

A view is a virtual table, it is the result of a SQL query. You can run queries on views as if they are tables.

Reasons to use views:
* When the DB is refactored, which leads to changes in queries, all queries running agains VIEWS are not affected. You only need to change the VIEW QUERY so that it still shows the same table.
* Security: Hide data by giving access to VIEWS with reduced columns and/or rows instead of the full table.
* Reusability: No need to type long complex queries, as some can be broken down into views.

Example
> CREATE VIEW monthly_sales AS
> SELECT ...

