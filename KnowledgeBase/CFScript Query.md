# ColdFusion with CFQueryParam
#coldfusion
## CFTags
```php
<cfquery name="news">
    SELECT id,title,story
    FROM news
    WHERE id = <cfqueryparam value="#url.id#" cfsqltype="cf_sql_integer">
</cfquery>
```

## CFScript 
``` php
queryObj = new Query(
 name="qryDemo",
 datasource="mydatasourcename",
 sql = "SELECT col1, col2
 FROM myTable
 WHERE id=:id"
); 
queryObj.addParam(name="id",value=arguments.id, cfsqltype="cf_sql_integer");
resultset=queryObj.execute().getResult();
```


## CFScript 
```php
queryObj = new Query(
 name="qryDemo",
 datasource="mydatasourcename",
 sql = "SELECT col1, col2
 FROM myTable
 WHERE id=:id"
); 
queryObj.addParam(name="id",value=arguments.id, cfsqltype="cf_sql_integer");
resultset=queryObj.execute().getResult();
```


- [[ColdFusion]]
