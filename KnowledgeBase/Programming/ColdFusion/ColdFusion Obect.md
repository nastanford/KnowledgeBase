# ColdFusion Object
#coldfusion #object

## Example

```php
component
  displayname = "Department Gateway"
  hint        = "I get the information about the department                 database table. Example a list of the departments."
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
  public function getDepartments()
  {
    var queryObj = new Query(
        name="test",
        datasource="#this.getDatasource()#",
        sql = "select * from department"
        );
    var results=queryObj.execute().getResult();
    return results;

  }

}
```
