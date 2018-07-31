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
