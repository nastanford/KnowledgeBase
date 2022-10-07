# PHP MS SQL Connection
#php 

## Config File Example MSSQL
```php
  <?php
    $DB_CONNECTION='sqlsrv';
    $DB_HOST='servername or IP';
    $DB_PORT='port';
    $DB_DATABASE='database';
    $DB_USERNAME='username';
    $DB_PASSWORD='password';
  ?>
```
## File
```php
<?php  
  $connectionInfo = 
  array("UID"=>$DB_USERNAME,"PWD"=>$DB_PASSWORD, "Database"=>$DB_DATABASE);
  $conn = sqlsrv_connect( $NDB_HOST, $connectionInfo);    
  $sql = "select * from tablename";
  // get results from database
  $result = sqlsrv_query( $conn, $sql);
  while( $row = sqlsrv_fetch_array($result))
  {
	/* Dump of the Row */
    var_dump($row);
    echo ('<hr>');
  }
?>
```