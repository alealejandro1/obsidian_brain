article_type:: [[SQL]]
summary::
keywords:: DELETE


# Statements of DML

## DELETE
Slower as it checks conditions and logs the effects, which will require logging the rollback.
Delete any number of rows
Does not recover memory
Index is kept and carries on from last increment

Example:
> DELETE FROM employee where ID = 1;


