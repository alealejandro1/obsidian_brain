article_type:: [[SQL]]
summary:: Its a collection of declarative SQL statements which can be CALL-ed with either no parameters or some parameters.
keywords:: Delimiter, Recursive Stored Procedures, Stack Overflow

Its a collection of declarative SQL statements which can be CALL-ed with either no parameters or some parameters.

Reasons to use:
* Less network traffic, only need to send the parameters
* Re-usability for all (just like functions)
* Security: Access to stored procedures but not the actual DB rows

# Delimiter
Because you need to give several statemetns, you need to change the delimiter so you can avoid executing them one-by-one

The default delimiter is ";" so  you can define another one (e.g. "$") and to organise the stored procedure. Once you are one, you restore the original delimiter ;

Example
> Delimiter $
> 	CREATE PROCEDURE My_Procedure(params)
> 	SQL queries;
> Delimiter ;

# Recursive Stored Procedures
[[Stack]] : Data Structure with Last In First Out (LIFO)

Items are pushed onto a stack and pop-ed off the stack

As a stored procedure calls itself (recursively), unless a base conditions becomes true and then the execution stops, this could lead to the procedure using memory until the system runs out of memory to hold the stack. This is Stack Overflow.