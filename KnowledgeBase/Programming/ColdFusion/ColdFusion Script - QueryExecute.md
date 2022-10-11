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

Example Object CF
```php 
component
  displayname = "Department Gateway"
  hint        = "I get the information about the department
                database table. Example a list of the departments."
  output      = "false"
  accessors   = "TRUE"  
{
  /* Properties */
  property name="datasource" type="string" default="";
  /* Constructor  */
  public function init(string datasource)
  {
    this.setDatasource(arguments.datasource);
    return this;
  }
  /* get Departments */
  public function getAll()
  {
    var queryObj = new Query(
        name="test",
        datasource="#this.getDatasource()#",
        sql = "select * from department"
        );
    var results=queryObj.execute().getResult();
    return results;
  }
  /* get by ID Departments */
  public function getById(id)
  {
    var queryObj = new Query(
        name="test",
        datasource="#this.getDatasource()#",
        sql = "select * from department where id = :id",
        params = {id:id}
        );
    queryObj.addParam(name="id",value=arguments.id, cfsqltype="cf_sql_integer");
    var results=queryObj.execute().getResult();
    return results;
  }
}
```


```php
<!--- Call CFC --->
<cfscript>
deptGateway = new appname.models.deptGateway(GetApplicationMetaData().datasource);
writeDump(deptGateway);

qry_dept = deptGateway.getById(170);
writeDump(qry_dept)
</cfscript>
  
```


- [[ColdFusion]]