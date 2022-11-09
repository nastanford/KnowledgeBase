- Turn off Debug when returning JSON data.
- You can use a CFC to get JSON to return with debug on.

### Example for ColdFusion 2018 
*(changes in 2021)*

```php
<!--- Turn off Debug when returning json data. --->
<cfsetting showDebugOutput="false">
<cfquery datasource="#Application.budget_officedb#" name="getumbclassdesc">    
  select EMPLID, NAME
  from DimEmpInfo
  Where ORG_LEVEL_E LIKE <cfqueryparam cfsqltype="CF_SQL_VARCHAR" value="%#url.id#%" />
  order by name    
</cfquery>
<cfset jsondata = serializeJSON(getumbclassdesc,"struct")>
<cfoutput>#trim(jsondata)#</cfoutput>
```

