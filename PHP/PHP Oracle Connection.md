# PHP Oracle Connection
#php 

## Config File
```php
<?php
  /* ODBC Connection */
  $connectionName = "odbc:OracleConnName";
  $username = "username";
  $password = "password";
?>
```

## File
```php
<?php  
try
{
  $conn = new PDO ($connectionName,$username, $password, array("encrypt" => 1,"trustServerCertificate" => 1));          
  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
  $sql="SELECT * FROM umab_general_person_vw fetch first 5 rows only";
  $result=$conn->prepare($sql);
  $result->execute();    
    echo ('<hr>');
    while ($row = $result->fetch(PDO::FETCH_ASSOC)) 
    {
      echo ($row['COLUMNNAME1'].' ');
      echo ($row['COLUMNNAME2'].' '.'<br>');
      echo ('<hr>');
    }
      // die(json_encode(array('outcome' => true)));
}
catch(PDOException $ex)
{
die(json_encode(array('outcome' => false, 'message' => 'Unable to connect')));
}
?>  
```

- [[PHP]]