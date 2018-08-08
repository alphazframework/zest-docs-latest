Site Maintenance library bundled with Zest Framework

# Site Maintenance
### Enable
There are two ways to enable maintenance mode (i.e., to show the user a message that the site is in maintenance mode).
##### Config file
In the configration file you need set Maintenance to `true`.
```php
/**
 * Default site maintainness.
 *
 * @var bool
    */
const Maintenance = true;
```
##### Dynamically
To enable maintenance mode dynamically you need to create site admins and create a method called `adminEnableMaintenance` in your Admin controller, and add the following in this method:
```php
maintenanceInstance()->updataMaintenance(true);
```
### Disable
There are two ways to disable maintenance mode.
##### Config file
In the configration file you need set Maintenance to `false`.
```php
/**
 * Default maintenance mode value.
 *
 * @var bool
 */
const Maintenance = false;
```
##### Dynamically
To disable maintenance mode dynamically you need to create site admins and create a method called `adminEnableMaintenance` in your Admin controller, and add the following in this method:
```php
maintenanceInstance()->updataMaintenance(false);
```
### Change the message
For changing the default message or style a little bit, open `503.php` from your views folder.
**path:** ../App/Views/errors/503.php

## Note:
Once maintenance mode is enabled via the configuration file, it will never be disabled by a dynamic process, but if the maintance disabled via the configuration file, it can be enabled and disabled by a dynamic process.
