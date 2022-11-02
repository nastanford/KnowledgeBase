Example 
```php
<script>
  async function getFaculty(select) {
    // if null value is selected, Stop Function
    if (select.value == "") {return;}
    // fetch the faculty data using the selected value
    const response = await fetch("filenameTest.php?value=" + select.value);
    // push the response text into the id facultyTable div
    document.getElementById("divid").innerHTML = await response.text();
  }
</script>
```