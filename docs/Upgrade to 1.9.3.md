# Upgrade to 1.9.3

## Upgrade core file
you can upgrade core file by running command
`composer update`
this command will automatically upgrade core file of zest framework

## Upgrade zest file
For updraging working file you need replace one file
- Replace Config.php *path:* **projectroot/Config/Config.php**
OR
- add these to the `Config.php` file
```php

/**
 * SMPT Host
 *
 * @var string
 */
const SMPT_HOST = "your-smtp-host";
/**
 * SMPT User
 *
 * @var string
 */    
const SMPT_USER = "your-smtp-user";
/**
 * SMPT Pass
 *
 * @var string
 */    
const SMPT_PASS = "your-smtp-pass";
/**
 * SMPT Port
 *
 * @var int
 */    
const SMPT_PORT = 111;

```

## Whats new in this update
http://zest.readthedocs.io/en/latest/mail/
