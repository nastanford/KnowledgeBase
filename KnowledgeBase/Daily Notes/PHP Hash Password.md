>Hashing is the standard way of protecting a user’s password before it’s stored in a database. Many common hashing algorithms like md5 and even sha1 are unsafe for storing passwords, because hackers can easily crack passwords hashed using those algorithms.

>PHP provides a built-in password hashing library that uses the bcrypt algorithm, currently considered the best algorithm for password hashing.

###### https://phpbestpractices.org/
```php
<?php
// Hash the password.  $hashedPassword will be a 60-character string.
$hashedPassword = password_hash('my super cool password', PASSWORD_DEFAULT);
// You can now safely store the contents of 
// $hashedPassword in your database!
// Check if a user has provided the correct 
// password by comparing what they typed with our hash
password_verify('the wrong password', $hashedPassword); // false
password_verify('my super cool password', $hashedPassword); // true
?>
```