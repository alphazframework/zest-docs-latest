Database management library bundled with Zest Framework

# Database management

## Configuration
In order to used database in zest framework you need config it properly
in Config.php you have to correct according to your details of your server.

```php
/**
 * Database host.
 *
 * @var string
 */
const DB_HOST = 'your-database-host';
/**
 * Database name.
 *
 * @var string
 */
const DB_NAME = 'your-database-name';
/**
 * Database user.
 *
 * @var string
 */
const DB_USER = 'your-database-user';

/**
 * Database password.
 *
 * @var string
 */
const DB_PASS = 'your-database-password';
```

### Simple example
Here is simple example follow:

```php
<?php

namespace App\Models;
use Softhub99\Zest_Framework\Database\MYSQL as DB;
use Config\Config;
class Post extends DB
{
	/* 
	* Store database name
	*/
	protected static $db_name = Config::DB_NAME;
	/* 
	* Store database table name
	*/
	protected static $db_tbl = 'posts';	
    public function name()
    {
        $db = new DB();
        $db->method(); //example code
    }
}
```

### Insert

For insert data into database you need call ```insert();``` method with parameters,The ```insert``` method return id on success boolean false on fail take a look at example:

```php
// rest code ...
/* 
* Store database name
*/
protected static $db_name = Config::DB_NAME;
/* 
* Store database table name
*/
protected static $db_tbl = 'posts';	
public function create($field1,$field2,$field3)
{
    $db = new DB();
   	//Prototype: $db->insert(table,dbName,params);
    $id = $db->insert(static::$db_tbl,static::$db_name,['field1'=>$field1,'field2'=>$field2,'field3'=>$field3]);
    //close the database connection, its recommanded
    $db->close();
    return $id;
}
// rest code ...
```

### Select
For selecting record you need just call ```select()``` method, take a look at following example:

```php
// rest code ...
/* 
* Store database name
*/
protected static $db_name = Config::DB_NAME;
/* 
* Store database table name
*/
protected static $db_tbl = 'posts';	
public function select()
{
    $db = new DB();
   	//Prototype: $db->insert(['db_name'=>'value','table'=>'value']);
    $result = $result = $db->select(['db_name'=>static::$db_name,'table'=>static::$db_tbl]);
    //close the database connection, its recommanded
    $db->close();
    return $result;
}
// rest code ...
```

### Select by where clause
For select records at specific condition or using where clause the method is same you just need passed wheres parameter take a look at example:

```php
// rest code ...
/* 
* Store database name
*/
protected static $db_name = Config::DB_NAME;
/* 
* Store database table name
*/
protected static $db_tbl = 'posts';	
public function select($id)
{
    $db = new DB();
   	//Prototype: $db->insert(['db_name'=>'value','table'=>'value']);
    $result = $result = $db->select(['db_name'=>static::$db_name,'table'=>static::$db_tbl,'wheres'=>['id = '.$id]]);
    //close the database connection, its recommanded
    $db->close();
    return $result;
}
// rest code ...
```
##### For multiple conditions
For using multiple wheres clause take a look at example:

```php
// rest code ...
    $result = $result = $db->select(['db_name'=>static::$db_name,'table'=>static::$db_tbl,'wheres'=>['id = '.$id,'userId ='.$userId]]);

// rest code ...
```

#### OrderBy 
For sorting orders you need passed orderby paramter take a look at example:

```php
// rest code ...
    $result = $result = $db->select(['db_name'=>static::$db_name,'table'=>static::$db_tbl,'order_by'=> 'id DESC']);
    //You can also passed id ASC , or you can also passed other then id column
// rest code ...
```  
#### Limits
For selecting limited records you need passed ```limit``` paramter take a look at example:

```php
// rest code ...
    $result = $result = $db->select(['db_name'=>static::$db_name,'table'=>static::$db_tbl,'limit' => ['start' => 3 , 'end' => 0]]);
    //start is the limit like 10
    //end is where to start 0 means start from beganning
    
// rest code ...
```  

#### Debug
For debuging or seeing the query you need to passe d ```debug``` parameter take a look at example:

```php
// rest code ...
    $result = $result = $db->select(['db_name'=>static::$db_name,'table'=>static::$db_tbl,'debug'=>'on']);
    //then it will var dump your query
    //like: 'SELECT * FROM users  WHERE id = 4';
    
// rest code ...
```  

### Delete
For deleting record in mysql we need called ```delete()``` method with id parameter, **Note: If id is not provided all record form specific tabel will be erased/deleted and this action never be undo.**
Here is following example:

```php
// rest code ...
/* 
* Store database name
*/
protected static $db_name = Config::DB_NAME;
/* 
* Store database table name
*/
protected static $db_tbl = 'posts';	
public function delete($id)
{
    $db = new DB();
   	//Prototype: $db->insert(['db_name'=>'value','table'=>'value','wheres'=>[]]);
    $result = $result = $db->delete(['db_name'=>static::$db_name,'table'=>static::$db_tbl,'wheres'=>['id = '.$id]]);
    $db->close();
    return $result;
}
// rest code ...
```
### Update
For updating records in database we need to called ```update``` method take a look at example:

```php
// rest code ...
/* 
* Store database name
*/
protected static $db_name = Config::DB_NAME;
/* 
* Store database table name
*/
protected static $db_tbl = 'posts';	
public function update($id,$uId)
{
    $db = new DB();
   	//Prototype: $db->insert(['db_name'=>'value','table'=>'value','columns'=>[],'wheres'=>[]]);
    $result = $result = $db->update(['db_name'=>static::$db_name,'table'=>static::$db_tbl,'columns'=>['useId'=>$uId,'update'=>time()],'wheres'=>['id = '.$id]]);
    $db->close();
    return $result;
}
// rest code ...
```

### Count
For count record in database we need to called ```count()``` method take a look at example

```php
// rest code ...
    $result = $result = $db->count(['db_name'=>static::$db_name,'table'=>static::$db_tbl]);  
// rest code ...
```  

### Create the database
For create the database we need to called ```createDb()``` method take a look at example 
```php
// rest code ...
    $result = $result = $db->createDb('phone');  
// rest code ...
```  

### Delete the database
For delete the database we need to called ```deleteDb()``` method take a look at example 
```php
// rest code ...
    $result = $result = $db->deleteDb('phone');  
// rest code ...
```  

### Create the table
For creating table we need to called ``` createTbl ```
 take a look at example:
```php
// rest code ...
    $result = $result = $db->deleteTbl('db|_name','sql');  
// rest code ...
```

### Delete the table
For delete the database we need to called ```deleteTbl()``` method take a look at example 
```php
// rest code ...
    $result = $result = $db->deleteTbl('db|_name','users');  
// rest code ...
```
