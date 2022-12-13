article_type:: SQL
summary::
keywords::

References a parent and child table. Is a[[Constraint]] used to maintain integrity of a DB.
The reference between tables can be set using the following reference options:

* CASCADE : UPDATE/DELETE in parent table -> Automatically UPDATE/DELETE on child table
* SET NULL: UPDATE/DELETE in parent table -> Foreign