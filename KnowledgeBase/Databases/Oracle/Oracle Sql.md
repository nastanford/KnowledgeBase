#oracle #sql #plsql

### Create Table Example
```sql
CREATE TABLE tablename 
(
  id Integer NOT NULL IDENTITY(1,1) PRIMARY KEY,
  name Varchar(50)
);
```


### Oracle Example SQL
```sql
/* Oracle 12 Syntax */
select * from links FETCH FIRST 10 ROWS ONLY;
select * from umb_links FETCH FIRST 10 ROWS ONLY;

/* Older Oracle Syntax */
select * from links WHERE ROWNUM <= 10;
select * from umb_links WHERE ROWNUM <= 10;

```