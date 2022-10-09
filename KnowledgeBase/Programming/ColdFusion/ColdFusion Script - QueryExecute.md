# ColdFusion Script - QueryExecute
#coldfusion 

```php
myQuery = queryExecute(
 "SELECT myCol1, myCol2 FROM myTable WHERE myCol1 = :myid ORDER BY myCol1 ASC ", 
  {myid: 5}, 
  {datasource = "myDSN"} 
);
writeDump(myQuery);
```


- [[ColdFusion]]