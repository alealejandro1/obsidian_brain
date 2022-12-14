article_type:: [[SQL]]
summary:: Maintains integrity of a DB, referencing tables with reference options such as CASCADE or RESTRICT
keywords:: [[Constraint]], Integrity, CASCADE, SET NULL, RESTRICT

Parent table has a certain column as [[Primary Key]] and Child table uses that column as Foreign Key.

References a parent and child table. Is a [[Constraint]] used to maintain integrity of a DB.
For [[MySQL]] the reference between tables can be set using the following reference options:

* CASCADE : UPDATE/DELETE in parent table -> Automatically UPDATE/DELETE on child table
* SET NULL: UPDATE/DELETE in parent table -> Foreign Key columns in a child table are SET to NULL
* RESTRICT: [[MySQL]] does not allow to UPDATE/DELETE any row from a parent table that has a matching row in a child table

![[Pasted image 20221213121406.png]]