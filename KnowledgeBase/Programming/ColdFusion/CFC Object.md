---
creation date: <% tp.file.creation_date() %>
type: programming
language: CFML
---
#coldfusion #cfc #object #oop

## Example Object CFC 
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

## Calling the Object
```php
<!--- Call CFC --->
<cfscript>
deptGateway = new appname.models.deptGateway(GetApplicationMetaData().datasource);
writeDump(deptGateway);

qry_dept = deptGateway.getById(170);
writeDump(qry_dept)
</cfscript>
  
```

