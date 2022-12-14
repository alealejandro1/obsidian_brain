article_type:: SQL
summary::
keywords::

Cursors are used in [[Stored Procedures]], [[SQL_triggers]] and [[SQL_functions]] to process a set of rows iteratively, where these rows are returned by a query. Cursors point at rows.

[[MySQL]] cursors are:
1. Read Only
2. Non Scrollable -> Traversed using row order from SELECT statement
3. Asensitive

SELECT STATEMENT produces a result set -> A cursor can be used to traverse and analyze that set line by line.

>DELIMITER $$
>CREATE PROCEDURE create_employee_list(
>	INOUT employee_list)