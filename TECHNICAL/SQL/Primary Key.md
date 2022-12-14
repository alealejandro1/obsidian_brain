article_type:: [[SQL]]
summary:: A [[Constraint]] for a column that will only accept NOT NULL UNIQUE data, used to link tables
keywords:: [[SQL Index]], UNIQUE, NOT NULL data, used to link tables

Is a [[Constraint]] for a column on a table. That column will only accept NOT NULL UNIQUE data. 
The PK constraint also creates a unique [[SQL Index]] for accessing the table faster. 
Guidance: Choose values that will never repeat, usually artificial values such as "Id Number"

Parent table has a certain column as [[Primary Key]] and Child table uses that column as [[Foreign Key]].