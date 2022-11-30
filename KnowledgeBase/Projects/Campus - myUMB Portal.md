## Action Items
- [x] IT Announcements - add a widget and still get original data
- [ ] Display of Links
	- [x] Title
	- [x] URL
	- [x] Start Date and End Date
	- [x] Alternate Link with Start and End Date/Time
	- [x] Is Active
	- [x] Security Type
	- [x] Keywords for Search?
- [ ] What's new widget if empty hide whole widget.
- [ ] Pull all external CSS and JS links in house to be stored on the server
- [ ] Move the CSS to Cloud and any other linked files
- [x] Create Alert Manual
- [x] Create Alert Admin Setting (manual for now as a new plan is being worked on for this.)
- [x]  new IT Announcements
- [x] Fixed Bug

*Manual maintenance message Make Admin for this in the future* (This is going to go away.)
```php
  <!--- TODO: Manual maintenance message Make Admin for this in the future --->
  <div>
    <cfset startDate = "10/14/2022 12:00:00">
    <cfset endDate = "10/14/2022 12:10:00">
  </div>
  <cfif DateCompare(startDate,now(),'n') lt 1 and DateCompare(endDate,now(),'n') gt -1 >
    <div class="col-12 alert-danger">
      <div class="col-6 offset-2 alert alert-danger d-flex align-items-center" role="alert">
        <div class="fw-bold h6">
          <i class="fa-duotone fa-triangle-exclamation h4"></i>
          Due to maintenance, please do not make any changes to your widget preferences from 8-9am on 10/15
        </div>
      </div>
    </div>
  </cfif>
```

## Git Rollback Example
git reset --hard 77f9f21340b3de5621e47d27b108e91209f519fd / git push origin branch --force
