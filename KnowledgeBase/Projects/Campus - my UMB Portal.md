## Action Items
- [x] Create Alert Manual
- [ ] Create Alert Admin Setting
- [ ] Pull all external CSS and JS links in house to be stored on the server
- [ ] IT Announcements - add a widget and still get original data
- [ ] Move the CSS to Cloud and any other linked files
- [ ] What's new widget if empty hide whole widget.


*Manual maintenance message Make Admin for this in the future*
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
 
