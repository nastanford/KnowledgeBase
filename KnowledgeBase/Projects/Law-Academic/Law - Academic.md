

## Tasks 
> *things with add/edit/delete may not be in banner.*
* Faculty Add/Edit/Delete

## Question
### People Type
**id - name**
1 -  Professor
2 -  Adjunct
3 -  Library
4 -  Other
5 -  BioOnly
6 -  Staff
7 - Clinical Instructor
8 - Faculty

### Dropdown for 
All      - 1,2,3,4,5,6,7
Faculty  - ?
Visiting - ?
emeriti  - ?
adjunct  - 2
other    - 4
library  - 3

## Deans
- Deans Should I add a Dean Type then add a way to select which type they are?
- Is there a desired Order?

### List
- Dean
- Senior Associate Dean
- Associate Deans
- Assistant Deans
- Faculty Directors of Academic Programs and Centers


# Faculty
Add Users  Automatically
===================== (no student employees)
SOLFAC - Faculty
SOLSTF - Staff
SOLAFL - Affiliate
Status updated if email is found with no UMBGUID - 
EMAIL to get UMBGUID 

If not in the directory allow adding manually and when the "email" is added check directory for umbguid.

Retired
- Barabra Gontrum - 12/31
- Peter Quint -

Make inActive: (Term Status or Overwritten Status)
If Terminated Change Status in app and move to another table so this can be overwritten.



Tables
========
Person 
PersonType

Person -  many to many - PersonType
- Faculty 
- Dean
- Staff
- Student

LDAP 
- ColdFusion Scheduled Task
- Remote Link Call to update as well

People - 
Get the ID's of current People in the law table
Get the law People that don't exist already 

List of people who do not yet have a UMBGUID,  Email Address
Look for anyone who has email but not umbguid 
