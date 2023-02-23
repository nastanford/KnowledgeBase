

# SQL Standards - Naming Conventions

## Table Names:

- Table names should be lowercase. Multiple words should be separated by an underscore.
- This is considered snake_case.
- Examples: "student","sol_student"
- Tables should be the singular form of a term.

## Columns:

- Column names should be lowercase. Column names should be descriptive of the content and fully written out.
- Examples: "deposit_distribution_type"
- Primary key ids should be written in following format: id.
- Foreign Key tablename_id
- This will make connecting foreign keys easier to understand.
- Example: "transaction_id"

### Most Tables will have the following columns at the end of the table:
- created_by varchar(10) not null,
- created_at datetime not null,
- updated_by varchar(10) null,
- updated_at datetime null
  
Note:
  The stakeholders may not need the updated fields initially, but it could be necessary in the future.  Note that the created_by and updated_by are varchar(10) representing the individual's umbguid. The two creation fields are mandatory and filled on record creation.

### SQL Table Requests
Make sure that you provide more than necessary for field data limits. This may save you time if the end user needs more capacity in the future. This might help you to avoid a table alteration later.

### Coding Standards for Coldfusion/PHP/JavaScript

  Note: PHP and JavaScript are case sensitive so it is important to be aware.

#### Variable Names:
- Variables should be written in camel case format. Try to avoid most if not all acronyms.
- Examples: 
```php
<cfset firstName="form.firstName">
```
- Not: 
```php
<cfset DOB="form.DOB">
```
- Do This: 
```php
<cfset dateOfBirth="form. dateOfBirth">
``` 
#### Variable Names:

# Query Files

- Query files should begin with qry, then the corresponding CRUD actions. These include insert, select, update, and remove.

**Example:**
- qry_transaction.cfm 
```sql
select * transactions where id = #
```

_The singular in the file name means we are getting only one record back and therefore we need the id to know which one._

- qry_transactions.cfm 
```sql
select * transactions
```

The plural file name means we are getting all of the records back for this table.

### Code File Naming Conventions:**

- File names should be lowercase and utilizing underscores. File names should be short and moderately descriptive. File names should not exceed 25 characters in length.

#### Example: 
"pregnantWorker.cfm" - camelCase

#### Example: 
"act_insert", “act_update” 

since these files do an action and should not display anything the user should never see these.


## ColdFusion

## PHP
### Classes: 
* /classes/person.class.php
* /classes/admin/person.class.php  

### included files: 
* /includes/person.inc.php


## MS SQL
