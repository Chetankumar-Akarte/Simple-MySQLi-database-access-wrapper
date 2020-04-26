# Simple-MySQLi-database-access-wrapper
Connect and query a MySQL database using MySQLi
In this document you can find proper usage of this library.

By - Chetankumar Akarte

For help email me - chetan.akarte@gmail.com

Get connected @ https://www.linkedin.com/in/chetanakarte

### About
This class is used to Connect and query a MySQL database using the MySQLi.extension.

### Requirements
- PHP: >=7.3.0

### Overview
This class library can read and parse a configuration file in the INI format and establishes a connection to a MySQL database server using connection parameters obtained from that configuration file.


### Usage
First you need to update config.ini with your database details and keep it in the same folder where your have db.php
```php
localhost = localhost 	//MySQL Host 
username = root		//MySQL User
password = ''		//MySQL Password
dbname = classic_news	//MySQL Database
```

Include db.php where you want to used MySQL data and initializa class.

```php
require_once('db.php');
$DB = new DB;
```

### Execute Query

```php
$query = "SELECT * tbl_category";
$DB->query($query);

```

### Process Query Result - 1st Row

```php
$query = "SELECT * tbl_category";
$get_cat = $DB->select($query);
	if(count($get_cat) > 0){
		$_cid= $get_cat[0]['cid'];
		$_catName = $get_cat[0]['category_name'];
		$_catStatus = $get_cat[0]['category_status'];
		$_imgDefault = $get_cat[0]['category_image'];
		$_catSequence = $get_cat[0]['category_sequence'];
		
	}
```

### Process Query Result - All Row

```php
$query = "SELECT * tbl_category";
$get_cat = $DB->select($query);
	if(count($get_cat) > 0){
	foreach ($category_check as $get_cat) {
		$_cid= $get_cat['cid'];
		$_catName = $get_cat['category_name'];
		$_catStatus = $get_cat['category_status'];
		$_imgDefault = $get_cat['category_image'];
		$_catSequence = $get_cat['category_sequence'];
		}
	}
```


### Fetch the last Insert Id from the database

```php
$query = "INSERT INTO tbl_news (featured, news_title, news_cat, news_description, news_cover_img,published_on) VALUES('".trim($_POST['isFeatured'])."','".trim($_POST['txtTitle'])."','".$_cid."','".$strDummy."','".$file_name."', now())";
	//echo $query;
	$DB->query($query);
	$_insetId=$DB->insert_id();
	//print_r($_insetId);
```
