---
creation date: <% tp.file.creation_date() %>
type: programming
language: CFML
---

# ColdFusion Script - QueryExecute
#coldfusion 

Example of query seen online.
```php
myQuery = queryExecute(
 "SELECT myCol1, myCol2 FROM myTable WHERE myCol1 = :myid ORDER BY myCol1 ASC ", 
  {myid: 5}, 
  {datasource = "myDSN"} 
);
writeDump(myQuery);
```

- [[ColdFusion]]