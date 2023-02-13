FYI – I’ve added notes to our document in the CF to cloud conversion folder so we can refer to it later for reference.  Here’s a summary of what is added:

**Subtracting/calculating differences between date fields** 

FYI - Current_Date is the current date defined in Oracle; GETDATE() in SQL server/Azure 

DATEDIFF is a function in SQL that calculates the difference between two dates. It takes three arguments: the unit of measure for the difference (such as day, week, month, or year), the start date, and the end date. The function returns an integer value that represents the number of units of measure between the two dates. 

Example (the previous way is commented out:  

```sql
select REQUESTID, User_UMBID, Requestor_UMBID, FIRSTNAME, LASTNAME, user_email, AFFILIATIONID, request_type, license_type, requestor_name, requestor_email, comments, REQUESTDATE, User_date, user_name, user_legal, user_FERPA, completed_date, completed_by, STATUS, needreview, needreviewbydate, reviewdate, reviewby 
from CRMRequest  
where status = 'Completed by SIMS' AND
	  active = 'Y' AND    
      (needReview is NULL or upper(needReview) != 'Y') 
/* AND 
(ReviewDate IS NOT NULL AND 
  (current_date - ReviewDate) > 330 OR ReviewDate IS NULL AND  
  (current_date - Completed_date) > 330
)
*/ 
AND (DATEDIFF(day, ReviewDate, GETDATE()) > 330)        OR (ReviewDate IS NULL AND DATEDIFF(day, Completed_date, GETDATE()) > 330)
```
