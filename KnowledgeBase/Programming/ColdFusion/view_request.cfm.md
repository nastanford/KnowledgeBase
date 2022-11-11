```php
<cfinclude template="/template2020/header.cfm">
<cfset pageTitle="Budget Office">
<cfinclude template="/budget_office/budget_amendment/nav.cfm">
<script src="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.6.0/js/bootstrap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.1/umd/popper.min.js"></script>
<link rel="stylesheet" href="scripts/jquery_ui/jquery-ui.css" />
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.js"></script>
<script src="https://cdn.datatables.net/1.10.22/js/jquery.dataTables.min.js"></script>
<script src="/scripts/jquery-3.1.1.min.js"></script>
<script src="/scripts/jquery_ui/jquery-ui.js"></script>
<script src="/scripts/validation/jquery.validate.js"></script>
<script src="/scripts/jquery.popupWindow.js"></script>
  
<script type="text/javascript">
  function denyClick(rad){
    var rads=document.getElementsByName(rad.name);
    document.getElementById('deniedDiv').style.display=(rads[0].checked)?'none':'block';
    document.getElementById('approvedDiv').style.display = 'none';
    document.getElementById('to_div0').style.display = 'none';    
  }
  function approveClick(rad){
    // if approved checked show approvedDiv div
    var rads=document.getElementsByName(rad.name);
    document.getElementById('deniedDiv').style.display = 'none';
    document.getElementById('approvedDiv').style.display=(rads[1].checked)?'none':'block';
    document.getElementById('to_div0').style.display=(rads[1].checked)?'none':'block';
  }  

  // Add Div from hidden Div
  function AddDiv()
  {
    // copy hidden div change name and add to main div

    var div0 = document.getElementById('div0');

    var div0Clone = div0.cloneNode(true);

    div0Clone.id = 'div' + (document.getElementById('main').childElementCount + 1);

    div0Clone.style.display = 'block';

    // rename input fields

    var inputs = div0Clone.getElementsByTagName('input');

    for (var i = 0; i < inputs.length; i++) {

      inputs[i].id = inputs[i].id + (document.getElementById('main').childElementCount + 1);

      inputs[i].name = inputs[i].name + (document.getElementById('main').childElementCount + 1);

    }

    // rename select fields

    var selects = div0Clone.getElementsByTagName('select');

    for (var i = 0; i < selects.length; i++) {

      selects[i].id = selects[i].id + (document.getElementById('main').childElementCount + 1);

      selects[i].name = selects[i].name + (document.getElementById('main').childElementCount + 1);

    }

    document.getElementById('main').appendChild(div0Clone);

    // rename label for fields

    var labels = div0Clone.getElementsByTagName('label');

    for (var i = 0; i < labels.length; i++) {

      labels[i].setAttribute('for', labels[i].getAttribute('for') + (document.getElementById('main').childElementCount));

    }

  }  

  

  // Add to Div from hidden Div

  function AddToDiv()

  {

    // copy hidden div change name and add to main div

    var todiv0 = document.getElementById('todiv0');

    var todiv0Clone = todiv0.cloneNode(true);

    todiv0Clone.id = 'div' + (document.getElementById('tomain').childElementCount + 1);

    todiv0Clone.style.display = 'block';

    // rename input fields

    var inputs =todiv0Clone.getElementsByTagName('input');

    for (var i = 0; i < inputs.length; i++) {

      inputs[i].id = inputs[i].id + (document.getElementById('tomain').childElementCount + 1);

      inputs[i].name = inputs[i].name + (document.getElementById('tomain').childElementCount + 1);

    }

    // rename select fields

    var selects = todiv0Clone.getElementsByTagName('select');

    for (var i = 0; i < selects.length; i++) {

      selects[i].id = selects[i].id + (document.getElementById('tomain').childElementCount + 1);

      selects[i].name = selects[i].name + (document.getElementById('tomain').childElementCount + 1);

    }

    document.getElementById('tomain').appendChild(todiv0Clone);

    // rename label for fields

    var labels = todiv0Clone.getElementsByTagName('label');

    for (var i = 0; i < labels.length; i++) {

      labels[i].setAttribute('for', labels[i].getAttribute('for') + (document.getElementById('tomain').childElementCount));

    }

  }  

  

  // get employees and update closest employee dropdown

  async  function getEmployees(dept)

  {

    // get current number for this div

    var divNum = dept.getAttribute("name").split("_")[2];

    // get selected value from department dropdown

    var deptId = document.getElementById(dept.id).value;

    // get employee from json qry_getEmployees.cfm

    var response = await fetch('qry_getEmployees.cfm?id=' + deptId);

    var employees = await response.json();

    // replace employee_# dropdown with employees

    var employeeSelect = document.getElementById('employees_' + divNum);

    // add new options

    var newOptions ="";

    for (var i = 0; i < employees.length; i++) {

      newOptions += '<option value="' + employees[i].EMPLID + '">' + employees[i].NAME + '</option>';      

    }

    employeeSelect.innerHTML = '<option value="">--Select--</option>';

    employeeSelect.innerHTML += newOptions;

  }

  // get employees and update closest employee dropdown

  async  function getToEmployees(dept)

  {

    // get current number for this div

    var divNum = dept.getAttribute("name").split("_")[1];

    // get selected value from department dropdown

    var deptId = document.getElementById(dept.id).value;

    // get employee from json qry_getEmployees.cfm

    var response = await fetch('qry_getEmployees.cfm?id=' + deptId);

    var employees = await response.json();

    // replace employee_# dropdown with employees

    var employeeSelect = document.getElementById('toemployees_' + divNum);

    // add new options

    var newOptions ="";

    for (var i = 0; i < employees.length; i++) {

      newOptions += '<option value="' + employees[i].EMPLID + '">' + employees[i].NAME + '</option>';      

    }

    employeeSelect.innerHTML = '<option value="">--Select--</option>';

    employeeSelect.innerHTML += newOptions;

  }

  

  // Delete the div

  function deleteDiv(btn) {

    var div = btn.parentNode.parentNode.parentNode;

    div.parentNode.removeChild(div);

    // due to removing a record updating the total amount

    updateAmount();

  }

  

  // Delete to the div

  function deleteToDiv(btn) {

    var div = btn.parentNode.parentNode.parentNode;

    div.parentNode.removeChild(div);

    // due to removing a record updating the total amount

    updateToAmount();

  }

  

  // Update the Amount

  function updateAmount() {

    var totalAmount = 0;

    // get all the inputs

    var inputs = document.getElementsByTagName('input');

    // loop through all inputs starts with amount and get amount

    for (var i = 0; i < inputs.length; i++) {

      if (inputs[i].id.startsWith('amount_')) {

        var amount = inputs[i].value;

        if (amount != '') {

          // If amount is a dollar amount or an amount with a decimal.

          totalAmount += parseFloat(amount);

        }

      }

    }

    // update total amount

    document.getElementById("FromTotalAmount").innerHTML = totalAmount;

    updateDifference();    

  }

  

  // Update the To Amount

  function updateToAmount() {

    var totalAmount = 0;

    // get all the inputs

    var inputs = document.getElementsByTagName('input');

    // loop through all inputs starts with amount and get amount

    for (var i = 0; i < inputs.length; i++) {

      if (inputs[i].id.startsWith('toamount_')) {

        var amount = inputs[i].value;

        if (amount != '') {

          // If amount is a dollar amount or an amount with a decimal.

          totalAmount += parseFloat(amount);

        }

      }

    }

    // update total amount

    document.getElementById("ToTotalAmount").innerHTML = totalAmount;

    updateDifference();    

  }

  

  function updateDifference() {

    // get FromTotalAmount

    var fromTotalAmount = document.getElementById("FromTotalAmount").innerHTML;

    console.log(fromTotalAmount);

    // get ToTotalAmount

    var toTotalAmount = document.getElementById("ToTotalAmount").innerHTML;

    console.log(toTotalAmount);

    // Update Difference Amount

    document.getElementById("DifferenceAmount").innerHTML = fromTotalAmount - toTotalAmount;

    console.log(fromTotalAmount - toTotalAmount);

  }

  

</script>

  

<style>

  .umbcf-container {width:100% !important;}

  .navbar{width:90% !important;}

  label {font-weight: bold;}

</style>

  

<cfoutput>

  

<!--- ==================================================================================================================--->

<!--- ==================================================================================================================--->

  <cfquery name="getRequest" datasource="#Application.budget_officedb#">

    select AMOUNT, BA_ID, COMMENTS, [FROM DEPT] as fromdept, [SUBMIT DATE] as submitdate, [TO DEPT] as todept, [REQUESTOR EMAIL] as reqmail, [REQUESTOR FIRSTNAME]as reqfirstname, [REQUESTOR LASTNAME] as reqlastname, STATUS

    from Factinitiator

    WHERE BA_ID = '#Url.BA_ID#'

  </cfquery>  

  <cfquery name="dimOrgELevel" datasource="#Application.budget_officedb#">

    SELECT distinct OrgLevelE_ID

    FROM [Dev_Quantum].[dbo].[DimOrg]

    where Org_Level_B in ('B0000000 - Institution Wide','B2000000 - Central Sector') and OrgLevelE_ID like'E%'

    order by OrgLevelE_ID

  </cfquery>  

  <cfquery name="dimobject" datasource="#Application.budget_officedb#">

    SELECT distinct ObjectID

    FROM [Dev_Quantum].[dbo].[DimObject]

    where objectid not like ('A%')

    and objectid not like ('b%')

    and objectid not like ('c%')

    and objectid not like ('d%')

    and objectid not like ('e%')

    and objectid not like ('z%')

  </cfquery>

  <h4>Budget Amendment Details</h4>

  <p>

    <strong>ID:</strong>  #getRequest.BA_ID#<BR>

    <strong>Submitter:</strong>  #getRequest.reqfirstname# #getRequest.reqlastname#<BR>

    <strong>Submit Date:</strong> #dateformat(getRequest.submitdate, 'mm/dd/yyyy')#<BR>

    <strong>From Dept:</strong>  #getRequest.fromdept#<BR>

    <strong>To Dept:</strong>  #getRequest.todept#<BR>

    <strong>Amount:</strong>  $#NumberFormat(getRequest.AMOUNT, '9.99')#<BR>

    <strong>Comments:</strong>  #getRequest.COMMENTS#

  </p>  

<!--- ==================================================================================================================--->

<!--- =================================== approve/deny =================================================================--->

<!--- ==================================================================================================================--->

<div class="border border-dark rounded p-2">

  <form action="view_request_action.cfm" name="add" id="frm" method="post" enctype="multipart/form-data">

<!---   <cfform action="view_request_action.cfm" name="add" id="frm" method="post" enctype="multipart/form-data"> --->

    <div class="row">

      <div class="col-sm-8">

        <div class="form-check">

          <input class="form-check-input" type="radio" name="admin_response" id="admin_response" value="Approved" tabindex="1" onclick="approveClick(this);">

          <label class="form-check-label" for="completed">Approve Request</label>

        </div>

        <div class="form-check">

          <input class="form-check-input" type="radio" name="admin_response" id="admin_response" value="Denied" tabindex="2" onclick="denyClick(this);">

          <label class="form-check-label" for="completed">Deny Request

          </label>

        </div>

        <div id="check5_validate"></div>

      </div>

    </div>

  

    <!--- ==================================================================================================================--->

    <!--- ==================================================================================================================--->

  

  <div id="deniedDiv" style="display: none">

    <div class="form-group row">

      <div class="col-12">

        <label class="col-form-label" for="lab_name">If Denied, enter email text to be sent to Requestor:</label>

        <textarea class="form-control" name="email_text" id="email_text" height="40" Width="200" aria-describedby="email_textHelp" aria-labelledby="email_text"></textarea>

      </div>

    </div>

  </div>        

</div>

  

<div id="approvedDiv" style="display: none">

  <div class="row mt-3">  

    <legend class="col-form-label col-sm-2 pt-0"><strong>Original Budget Amendment?</strong></legend>

    <div class="col-sm-3">

      <div class="form-check form-check-inline">

        <input class="form-check-input" type="radio" name="org_ba" id="org_ba" value="Yes" data-error="##errNm4" tabindex="3">

        <label class="form-check-label" for="org_ba">Yes</label>

      </div>

      <div class="form-check form-check-inline">

        <input class="form-check-input" type="radio" name="org_ba" id="org_ba" value="No" data-error="##errNm4" tabindex="4" checked>

        <label class="form-check-label" for="org_ba">No</label>

      </div>

      <div id="check5_validate"></div>

    </div>

  </div>

  <div class="bg-secondary rounded-top text-white p-1"><h6>From:</h6></div>  

    <div class="border border-secondary rounded-bottom p-4">

<!--- ==================================================================================================================--->

    <!--- ************************************ --->

    <!---    Hidden                            --->

    <!--- ************************************ --->

    <div id="div0" style="display: none" class="mt-2">

      <div class="row">

        <div class="col-1">

          <label for="dept_">Department</label>

            <select class="form-control" name="from_dept_" id="from_dept_" onChange="getEmployees(this)">

              <option value="">--select--</option>

              <cfloop query="#dimOrgELevel#">

                <option value="#replace(OrgLevelE_ID,'E','')#">#OrgLevelE_ID#</option>

              </cfloop>

            </select>

          </div>

        <div class="col-2">

          <label for="soapf_" class="fw-bold">SOAPF</label>

          <input type="text" name="soapf_" id="soapf_" placeholder="" class="form-control" />

        </div>

        <div class="col-1">

          <label for="fromObject_" class="fw-bold">Object</label>

          <select class="form-control" name="fromObject_" id="fromObject_">

            <option value="">--select--</option>

            <cfloop query="#dimobject#">

              <option value="#ObjectID#">#ObjectID#</option>

            </cfloop>

          </select>

        </div>

        <div class="col-1">

          <label for="amount_" class="fw-bold">Amount</label>

          <input type="text" name="amount_" id="amount_" placeholder="" class="form-control" onChange="updateAmount()" />

        </div>

        <div class="col-1">

          <label for="fte_" class="fw-bold">FTE</label>

          <input type="text" name="fte_" id="fte_" placeholder="" class="form-control" />

        </div>

        <div class="col-1">

          <label for="PostionNum_" class="fw-bold">Postion ##</label>

          <input type="text" name="PostionNum_" id="PostionNum_" placeholder="" class="form-control" />

        </div>

        <div class="col-2">

          <label for="employees_" class="fw-bold">Employees</label>

          <select name="employees_" id="employees_" class="form-control">

            <option value="">--Select--</option>

          </select>

        </div>

        <div class="col-2">

          <label for="comments_" class="fw-bold">Comments</label>

          <input type="text" name="comments_" id="comments_" placeholder="" class="form-control" />

        </div>

        <div class="col-1">

          <button type="button" class="btn btn-secondary float-right mt-4" onclick="deleteDiv(this)">X</button>

        </div>

      </div>

    </div>    

    <!--- ************************************ --->

    <!---    Hidden                            --->

    <!--- ************************************ --->

    <div id="todiv0" style="display: none" class="mt-2">

      <div class="row">

        <div class="col-1">

          <label for="todept_">Department</label>

            <select class="form-control" name="todept_" id="todept_" onChange="getToEmployees(this)">

              <option value="">--select--</option>

              <cfloop query="#dimOrgELevel#">

                <option value="#replace(OrgLevelE_ID,'E','')#">#OrgLevelE_ID#</option>

              </cfloop>

            </select>

          </div>

        <div class="col-2">

          <label for="tosoapf_" class="fw-bold">SOAPF</label>

          <input type="text" name="tosoapf_" id="tosoapf_" placeholder="" class="form-control" />

        </div>

        <div class="col-1">

          <label for="toObject_" class="font-weight-bold">Object</label>

          <select class="form-control" name="toObject_" id="toObject_">

            <option value="">--select--</option>

            <cfloop query="#dimobject#">

              <option value="#ObjectID#">#ObjectID#</option>

            </cfloop>

          </select>

        </div>

        <div class="col-1">

          <label for="toamount_" class="fw-bold">Amount</label>

          <input type="text" name="toamount_" id="toamount_" placeholder="" class="form-control" onChange="updateToAmount()" />

        </div>

        <div class="col-1">

          <label for="tofte_" class="fw-bold">FTE</label>

          <input type="text" name="tofte_" id="tofte_" placeholder="" class="form-control" />

        </div>

        <div class="col-1">

          <label for="toPostionNum_" class="fw-bold">Postion ##</label>

          <input type="text" name="toPostionNum_" id="toPostionNum_" placeholder="" class="form-control" />

        </div>

        <div class="col-2">

          <label for="toemployees_" class="fw-bold">Employees</label>

          <select name="toemployees_" id="toemployees_" class="form-control">

            <option value="">--Select--</option>

          </select>

        </div>

        <div class="col-2">

          <label for="tocomments_" class="fw-bold">Comments</label>

          <input type="text" name="tocomments_" id="tocomments_" placeholder="" class="form-control" />

        </div>

        <div class="col-1">

          <button type="button" class="btn btn-secondary float-right mt-4" onclick="deleteDiv(this)">X</button>

        </div>

      </div>

    </div>    

    <!--- ************************************ --->

    <!---    End Hidden                        --->

    <!--- ************************************ --->

<!--- ==================================================================================================================--->

  

    <div id="main">

      <div id="div1" class="">

        <div class="row">

          <div class="col-1">

            <label for="dept_1">Department</label>

            <select class="form-control" name="from_dept_1" id="from_dept_1" onChange="getEmployees(this)">

              <option value="">--select--</option>

              <cfloop query="#dimOrgELevel#">

                <option value="#replace(OrgLevelE_ID,'E','')#">#OrgLevelE_ID#</option>

              </cfloop>

            </select>

          </div>

          <div class="col-2">

            <label for="soapf_1" class="fw-bold">SOAPF</label>

            <input type="text" name="soapf_1" id="soapf_1" placeholder="" class="form-control" />

          </div>

          <div class="col-1">

            <label for="fromObject_1" class="font-weight-bold">Object</label>

            <select class="form-control" name="fromObject_1" id="fromObject_1">

              <option value="">--select--</option>

              <cfloop query="#dimobject#">

                <option value="#ObjectID#">#ObjectID#</option>

              </cfloop>

            </select>

          </div>

          <div class="col-1">

            <label for="amount_1" class="fw-bold">Amount</label>

            <input type="text" name="amount_1" id="amount_1" placeholder="" class="form-control" onChange="updateAmount()" />

          </div>

          <div class="col-1">

            <label for="fte_1" class="fw-bold">FTE</label>

            <input type="text" name="fte_1" id="fte_1" placeholder="" class="form-control" />

          </div>

          <div class="col-1">

            <label for="PostionNum_1" class="fw-bold">Postion ##</label>

            <input type="text" name="PostionNum_1" id="PostionNum_1" placeholder="" class="form-control" />

          </div>

          <div class="col-2">

            <label for="employees_1" class="fw-bold">Employees</label>

            <select name="employees_1" id="employees_1" class="form-control">

              <option value="">--Select--</option>

            </select>

          </div>

          <div class="col-2">

            <label for="comments_1" class="fw-bold">Comments</label>

            <input type="text" name="comments_1" id="comments_1" placeholder="" class="form-control" />

          </div>

            <div class="col-1">

            <button type="button" class="btn btn-secondary float-right mt-4" onclick="deleteDiv(this)">X</button>

          </div>

        </div>

      </div>    

    </div>    

    <div class="row mt-2">      

      <div class="col-12">

        <button type="button" tabindex="4" id="btn0" class="btn btn-secondary btn-sm mt-4" onClick="AddDiv()"><i class="fa-solid fa-plus"></i> Add</button>

      </div>

    </div>

  </div>

    <!---  Balance  --->

    <!--- ==================================================================================================================--->

    <div class="form-group row" role="field">

      <div class="mb-2 ml-2 p-2">

        <strong>From: </strong>

        $<span id="FromTotalAmount">0</span>

        <strong>To: </strong>

        $<span id="ToTotalAmount">0</span>

        <strong>Difference: </strong>

        $<span id="DifferenceAmount">0</span>

      </div>

    </div>  

  </div>

  <!--- ==================================================================================================================--->

  <div id="to_div0" style="display:none" class="mt-2">

    <div class="bg-secondary rounded-top text-white mt-2 p-1"><h6>To:</h6></div>    

      <div class="border border-secondary rounded-bottom p-4">

        <div id="tomain">

          <div id="todiv1" class="">

            <div class="row">

              <div class="col-1">

                <label for="todept_1">Department</label>

                <select class="form-control" name="todept_1" id="todept_1" onChange="getToEmployees(this)">

                  <option value="">--select--</option>

                  <cfloop query="#dimOrgELevel#">

                    <option value="#replace(OrgLevelE_ID,'E','')#">#OrgLevelE_ID#</option>

                  </cfloop>

                </select>

              </div>

              <div class="col-2">

                <label for="tosoapf_1" class="fw-bold">SOAPF</label>

                <input type="text" name="tosoapf_1" id="tosoapf_1" placeholder="" class="form-control" />

              </div>

              <div class="col-1">

                <label for="toObject_1" class="font-weight-bold">Object</label>

                <select class="form-control" name="toObject_1" id="toObject_1">

                  <option value="">--select--</option>

                  <cfloop query="#dimobject#">

                    <option value="#ObjectID#">#ObjectID#</option>

                  </cfloop>

                </select>

              </div>

              <div class="col-1">

                <label for="toamount_1" class="fw-bold">Amount</label>

                <input type="text" name="toamount_1" id="toamount_1" placeholder="" class="form-control" onChange="updateToAmount()" />

              </div>

              <div class="col-1">

                <label for="tofte_1" class="fw-bold">FTE</label>

                <input type="text" name="tofte_1" id="tofte_1" placeholder="" class="form-control" />

              </div>

              <div class="col-1">

                <label for="toPostionNum_1" class="fw-bold">Postion ##</label>

                <input type="text" name="toPostionNum_1" id="toPostionNum_1" placeholder="" class="form-control" />

              </div>

              <div class="col-2">

                <label for="toemployees_1" class="fw-bold">Employees</label>

                <select name="toemployees_1" id="toemployees_1" class="form-control">

                  <option value="">--Select--</option>

                </select>

              </div>

              <div class="col-2">

                <label for="tocomments_1" class="fw-bold">Comments</label>

                <input type="text" name="tocomments_1" id="tocomments_1" placeholder="" class="form-control" />

              </div>

                <div class="col-1">

                <button type="button" class="btn btn-secondary float-right mt-4" onclick="deleteDiv(this)">X</button>

              </div>

            </div>

          </div>    

        </div>    

        <div class="row mt-2">      

          <div class="col-12">

            <button type="button" tabindex="4" id="btn0" class="btn btn-secondary btn-sm mt-4" onClick="AddToDiv()"><i class="fa-solid fa-plus"></i> Add</button>

          </div>

        </div>

      </div>

    </div>

  </div>

</div>

  <div class="row">      

    <div class="col-12 ml-5">      

        <button type="submit" class="btn btn-secondary btn-sm" tabindex="15">Submit</button>

    </div>

  </div>

</form>

<!--- </cfform> --->

  

</cfoutput>

  
<cfinclude template="/template2020/footer.cfm">
```