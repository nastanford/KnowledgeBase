#project #oem #cooptools #tasks

## My Items

- [x] Version of - record of change
- [x] Update Approved need it to be Y/N and Null
- [x] Leadership Succession - Update column name position to title - Sent to dba's
- [x] Essential Processes - Add Table for Time Sensitivity - Sent to dba's
- [x] Leadership Succession - CRUD (Max: 3 - Primary, Secondary, Tertiary)
- [x] Essential Processes - CRUD
- [x] Essential Processes - 
- [x] Essential Processes - People - Database Process_id
- [x] Essential Processes - People - CRUD
- [x] Essential Processes - Places - CRUD
- [x] Essential Processes - Things - CRUD
- [x] Contact Roster - CRUD
- [x] Additional Information - CRUD
- [x] Record of Change - CRUD
- [ ] CSV File - What is the layout of the CSV
- [ ] Plan - HTML
- [ ] Plan - PDF
- [ ] Plan - CSV
- [ ] Create Admin for Users or Use Current one with if statements.
- [ ] DeptRoleType Security
- [ ] Add Signature Table
- [ ] Add Signature Code
- [ ] Signature inactive
- [ ] Check Requests only show - Departments user has rights too
- [ ] Check Requests Red Circle Count
- [ ] Check Users only show - Departments user has rights too

edit user admin

### Test Roles
#### Approved
- [ ] Admin
- [ ] Approver
- [ ] Planner
- [ ] View Only

```php
<!---
0. Webdev
  WebDev= Yes/No
  select *
  from usergroup
  WHERE GROUP_NAME = 'WEBDEV';
--->

<cfquery name="" datasource="#websec#">
  SELECT *
  FROM usergroup
  WHERE GROUP_NAME = 'WEBDEV'
</cfquery>
<!---
1. Check to see if AppAdmin vs User
  AppAdmin= Yes/No

  select *
  from usergroup
  WHERE GROUP_NAME LIKE 'WEBDEV%';
--->
<cfquery name="" datasource="#websec#">
  SELECT *
  FROM usergroup
  WHERE GROUP_NAME = 'COOPTOOL_ADMIN'
</cfquery>
<!---
2. Check to see what role types for what departments
  DepartmentRoleType =
    - DepartmentID
    - RoleType
  --->
```
## Action Items
### Essential Process: 
1.  [x]  Replace “Leadership Succession Table” with “Essential Processes”
2.  [x]  Typo under Continuity Strategies, “preforms” should be “performs”
3.   [ ] TimeSensitivity should be a drop down….is it already? If not, please add as options: Immediately, Within a few days, Within a couple week, and In a month or more. 
- (Done on Development but waiting for insert permissions on Production.)
- Waiting on DBA's to get the table done for Processes so I can input the new TimeSensitivity.
- [ ] i. Dropdown should be applied (or auto-populated) for time-sensitivity in Essential Job Aids too.

### Essential Process Job Aids: **Authorities**

1.  [ ] Replace “authorities” with “responsibilities and authorities” and amend the text language to describe authorities and responsibilities when performing this process.
2.  [ ] Add “limitations” and put text language that says: “describe limitations of responsibilities and authorities for backup personnel.”

### Essential Process Job Aids: **Continuity of Resources**

1.  [ ] There should be three areas within this section along with the text

 - [ ]  i.  Critical Applications & Vital Records: Applications and records that are needed and describe strategies to safeguard and preserve them i.e., cloud-based services, manual workarounds, hard copies etc

 -  [ ] ii. Communication Resources: Comms. resources needed and strategies for redundancy or safeguarding.

-  [ ] iii. Equipment: What equipment or resource is needed and describes strategies to safeguard its availability.

### Essential Process Job Aids: **Process description**

 - [ ] 1.  Remove the second “process description” listed underneath “instructions or procedures…”

### Safeguard of critical applications and vital records

- [ ]  1.  It should state the first two sentences as text but add a fillable box for this section.
- [ ] 2.  This is a standalone section (not related to Additional Information)

### Additional Information

- [ ] 1.  This is an optional section and should not appear if “additional information” is not attached/uploaded to the plan
- [ ] 2.  This section allow depts to add attachments to their plan, for example: contact lists, standard operating procedures etc.

### Laura Notes
- [ ] 1.  Hayley, I think the Concept of Operations section needs a section that makes it clear who is doing what and how the differentiation between those sections are determined. I would struggle to implement the plan if I were department continuity personnel. It should probably be in a format like if this then this, sort of like our duty officer checklists.
- [ ] 2.  Nathan, I don’t think the Contact Roster table should be called “Leadership Succession Table”, perhaps “Contacts Roster”. I’d like to see a column in that table that specifies the role the person has in the plan (e.g. Primary Essential Process 1, Secondary Essential Process 3, etc. ).
- [ ] How do we access the data in the COOP tool? Will it be able to integrate with SmartSheet? Will it export via csv to be imported into SmartSheet? I’m thinking for analysis purposes. It’d be most useful to be able to easily get the data into both Excel and SmartSheet. - Going to need to know what FORMAT the CSV file will be?  What columns and what data?

### More Changes
- [ ] Create a CRUD Screen for Time Sensitivity Table

### List
- Leadership Succession
- Essential Processes
- Essential Processes Job Aids
    - Safeguard of Critical Applications and Vital Records
- Contact Roster
- Additional Information (Attached Documents) 


```php
<nav style="--bs-breadcrumb-divider: '>';" aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item">
    <a href="#">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>
```