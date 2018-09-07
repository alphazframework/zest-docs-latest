# Dependency Injection

Zest framework provides IoC to load dependent classes automatically.

### Where to define
Go to `Config/Dependencies.php`

You should see something like the following:

```php
<?php

    /*
     * class that should be automatically loaded
     */
return
    [
        'version' => new \Zest\Common\Version(),
        //define more if you want
    ];

```

### Get the class in your method/view or controller

```php
$d = new \Zest\Common\Container\DIS();
echo $d->get('version')::VERSION;
```

