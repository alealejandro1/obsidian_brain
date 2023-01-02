article_type:: [[SQL]]
summary:: Cursors are used in [[Stored Procedures]], [[SQL_triggers]] and [[Functions in SQL]] to process a set of rows iteratively, where these rows are returned by a query. Cursors point at rows.
keywords:: Stored Procedure, Cursor, Read Only, Row by Row

[[MySQL]] cursors are:
1. Read Only
2. Non Scrollable -> Traversed using row order from SELECT statement
3. Asensitive

SELECT STATEMENT produces a result set -> A cursor can be used to traverse and analyze that set line by line.

Flow of how cursor work:
	1. Declare
	2. Open
	3. Fetch
		IF not empty: Keep fetching
		IF empty: Close

Below is the definition of a stored procedure to create employee list:

>	DELIMITER \$$
	 CREATE PROCEDURE create_employee_list(
		INOUT employee_list VARCHAR(400))
	BEGIN
		DECLARE finished INTEGER default 0;
		DECLARE employee_name VARCHAR(30) DEFAULT "";
		DECLARE curName
			CURSOR FOR SELECT name FROM EMPLOYEE;
		DECLARE CONTINUE HANDLER
			FOR NOT FOUND SET finished =1;
		OPEN curName;
		get Name: LOOP
			FETCH curName INTO employee_name;
			IF finished=1 THEN LEAVE getName; END IF;
		SET EMPLOYEE_LIST = CONCAT(employee_name, ';', employee_list)
		END LOOP getName;
		CLOSE curName;
	END \$$
	DELIMITER;

Below is how the stored procedure is called using the cursor @:
>SET @curName = "";
>CALL create_employee_list(@curName)
>SELECT @curName


