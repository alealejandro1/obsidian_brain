article_type:: [[SQL]]
summary:: Not granular, has effects on memory
keywords:: TRUNCATE, DROP


# Statements of DDL

## TRUNCATE
* Deletes ALL rows, very fast because it doesn't care
* Resets table, index is restarted --> but the table structure and its columns, [[constraint]], [[SQL Index]], and so on remain
* Recovers memory --> Cannot rollback
* Table is preserved, but empty
* No triggers are fired


EXAMPLE:
> TRUNCATE employee;


## DROP
* Not only deletes all rows, but removes the table, which includes indexes, [[SQL View]], [[Stored Procedures]], etc.
* No triggers are fired
* Cannot [[Rollback]]
EXAMPLE
> DROP TABLE employee;
