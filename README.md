# Syversoft README - MSSQL (Microsoft SQL Server)

**SQL Snippets**

**1. Create new column into a table**
```
ALTER TABLE myTable ADD myColumn int;
ALTER TABLE myTable ADD myColumn varchar(100);
ALTER TABLE myTable ADD myColumn datetime NULL;
ALTER TABLE myTable ADD myColumn int NOT NULL DEFAULT(1);
```
**2. Get column name based on table name**
```
SELECT COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME like '%myTable%'
```
**3. Get table name based on column name**
```
SELECT TABLE_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE COLUMN_NAME like '%myColumn%'
```
**4. Search for store procedure that contains a specific text**
```
USE YourDatabaseName;

DECLARE @SearchText NVARCHAR(MAX) = N'I Have a House';

SELECT OBJECT_NAME(object_id) AS 'Stored Procedure Name'
FROM sys.sql_modules
WHERE OBJECTPROPERTY(object_id, 'IsProcedure') = 1
    AND definition LIKE '%' + @SearchText + '%';
```
