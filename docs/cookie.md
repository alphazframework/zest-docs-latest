Cookie Management library bundled with Zest Framework

# Cookie Management

## Configuration
There is no configuration need for using session library in zest framework 
### Set
For setting the cookie and its value you need to used ```set_cookie()``` function take a look at an example:

```php
<?php

namespace App\Models;
class users
{

    public function login()
    {
        //its prototype is set_cookie($name, $value, $expire, $path, $domain, $secure, $httponly);
        set_cookie("test", "bla", 3600, "/", $_SERVER['SERVER_NAME'], true, false);
        //return boolean, true | false
    }
}
```
### Get
To get the cookie value you need to used ```get_cookie()``` function take a look at an example:

```php
<?php
namespace App\Models;
class users
{

    public function getLogin()
    {
        //its prototype is get_cookie("name");
        get_cookie('users');
        //return value on success  boolean false on fail
    }
}
```

### Delete
For deleting the cookie value you need to used ```delete_cookie()``` function take a look at example:

```php
<?php

namespace App\Models;
class users
{

    public function logout()
    {
        //its prototype is delete_cookie("name");
        delete_cookie('users');
        //return boolean, true | false
    }
}
```

### Check
For checking is cookie is set or exists you need to used ```is_cookie()``` fuunction take a look at an example:


```php
<?php

namespace App\Models;
class users
{

    public function isLogin()
    {
        //its prototype is is_cookie("name");
        is_cookie('users');
        //return boolean, true | false
    }
}
```
