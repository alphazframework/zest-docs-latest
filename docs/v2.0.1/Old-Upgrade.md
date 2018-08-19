# Upgrade to 1.9.4

## Upgrade core file
You can upgrade core files by running the command:
`composer update`
This command will automatically upgrade the core files of Zest framework.

## Upgrade Zest files

You just need to add one file in this update
Download this file https://github.com/Softhub99/Zest/blob/master/Zest
and add to the root directory

If you want update the version correct it form
https://github.com/Softhub99/Zest/blob/master/Config/Config.php#L22

## What's new in this update
http://zest.readthedocs.io/en/latest/console/

# Upgrade to 1.9.3

## Upgrade core file
You can upgrade core files by running the command:
`composer update`
This command will automatically upgrade the core files of Zest framework.

## Upgrade Zest files
For upgrading working files, you need replace one file:
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

## What's new in this update
http://zest.readthedocs.io/en/latest/mail/


# Upgrade to 1.9.1

## Upgrade core file
You can upgrade core files by running this command
`composer update`
This command will automatically upgrade the core files of Zest framework.

## Upgrade zest file
For upgrading working files, you need replace the following files.
- Replace Config.php *path:* **projectroot/Config/Config.php**
- Replace system.php *path:* **projectroot/system.php**
- Add `$router->cacheRouters();` Above `$router->dispatch($_SERVER['QUERY_STRING']);` in your routes.php
