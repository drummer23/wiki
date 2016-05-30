#SQL

##Show Information

Shows the SQL Statement to (re)create the Table:

```sql
SHOW CREATE TABLE mytable
```

##Contraints

Enables/Disable Key Contraints

```sql
SET FOREIGN_KEY_CHECKS = {1|0};
```

##Dumps

Backup
```sql
mysqlump [db_name] > dumpfilename.sql
```

Restore
```sql
mysql [db_name] < dumpfilename.sql
```

From another Server
```sql
 ssh [user]@[server] mysqldump [sourcedb] | mysql --database=[targetdb]
```

##Select

```sql
SELECT
	p.name, o.name
FROM
	Person p
	JOIN Ort o ON o.id=p.ortId
WHERE
	o.name IN ('Uster', 'Winterthur')
ORDER BY
	p.name
```

##Insert

```sql
INSERT INTO
	Customers (Customer_Name, City, Country)
VALUES
	('Cardinal', 'Stavanger', 'Norway');
```
