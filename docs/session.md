Session handling library bundled with Zest Framework

# Session Handling

## Configuration
There is no configuration need used session library in zest framework  but if you want change session storage path in Config.php you have to change according to your details of your server.

```php
/**
 * Default Session storage path.
 *
 * @var string
 */
const Session_Path = '../Storage/Session/';
```

### Set
For setting the session and its value you need to used ```setValue()``` method take a look at example:

```php
<?php

namespace App\Models;
use Softhub99\Zest_Framework\Session\Session;
class users
{

    public function login()
    {
        //its prototype is Session::setvalue("name","value");
        Session::setValue('users',11223);
        //return boolean, true | false
    }
}
```
### Get
For get the session value you need to used ```getValue()``` method take a look at example:

```php
<?php

namespace App\Models;
use Softhub99\Zest_Framework\Session\Session;
class users
{

    public function getLogin()
    {
        //its prototype is Session::getValue("name");
        Session::getValue('users');
        //return value on success  boolean false on fail
    }
}
```

### Delete
For deleting the session value you need to used ```unsetValue()``` method take a look at example:

```php
<?php

namespace App\Models;
use Softhub99\Zest_Framework\Session\Session;
class users
{

    public function logout()
    {
        //its prototype is Session::unsetValue("name");
        Session::unsetValue('users');
        //return boolean, true | false
    }
}
```

### Check
For checking is session is active you need to used ```unsetValue()``` method take a look at example:

```php
<?php

namespace App\Models;
use Softhub99\Zest_Framework\Session\Session;
class users
{

    public function isLogin()
    {
        //its prototype is Session::isSession("name");
        Session::isSession('users');
        //return boolean, true | false
    }
}
```
