# Exploit Title: Courier Management System 1.0 - 'First Name' Stored XSS
## Exploit Author: Zhaiyi (Zeo)
## Date: 2020-12-11
## Google Dork: N/A
## Vendor Homepage: https://www.sourcecodester.com/php/14611/courier-management-system-using-phpmysqli-source-code.html
## Software Link: https://www.sourcecodester.com/download-code?nid=14611&title=Courier+Management+System+using+PHP%2FMySQLi+with+Source+Code
## Affected Version: Version 1
## Category: Web Application

Step 1: Log in to the CMS with any valid user credentials.

Step 2: Click on the logged in username on header and select Manage Account.

Step 3: Rename the user First Name or Last Name to"<script>alert(1111)</script>".

Step 4: Update Profile and this will trigger the XSS.

Step 5: Logout and login again and the page will display the domain name.


![image-20201214105633308](https://gitee.com/godzeo/blogimg/raw/master/img/20201214105633.png)
![image](https://user-images.githubusercontent.com/38218756/102035425-47770480-3dfb-11eb-9b48-0e03ff25b6d5.png)
