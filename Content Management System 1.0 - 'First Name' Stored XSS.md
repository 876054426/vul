

```
# Exploit Title: Content Management System 1.0 - 'First Name' Stored XSS
# Exploit Author: Zhayi (Zeo)
# Date: 2020-12-14
# Vendor Homepage: https://www.sourcecodester.com/php/14625/content-management-system-using-phpmysqli-source-code.html
# Software Link: https://www.sourcecodester.com/download-code?nid=14625&title=Content+Management+System+using+PHP%2FMySQLi+with+Source+Code
# Affected Version: Version 1
# Category: Web Application
# Tested on: WINDOWS 10


Step 1: Log in to the CMS with any valid user credentials.
Step 2: Click on the logged in username on header and select Manage Account.
Step 3: Rename the user First Name to "<script>alert(document.domain)</script>".
Step 4: Update Profile and this will trigger the XSS.
Step 5: Logout and login again and the page will display the domain name.
```

![image-20201214161339780](https://gitee.com/godzeo/blogimg/raw/master/img/20201214161339.png)