Site Maintenance library bundled with Zest Framework

# Site Maintenance
### Enable 
For Enable the site maintenance which means user seen message the site is in the maintenance mode there are two way
##### Config file
In the configration file you need set Maintenance to true for enable
```php
/**
 * Default site maintainness.
 *
 * @var bool
    */
const Maintenance = true;
```
##### Dynamically 
For update site maintenance dynamically you need to create site admins and create method called adminEnableMaintenance in your Admin controller add following in this method:
```php 
maintenanceInstance()->updataMaintenance(true);
```
### Disable 
For Disable the site maintenance which means user not seen message the website is in maintenance mode there are two way
##### Config file
In the configration file you need set Maintenance to false for disalbe
```php
/**
 * Default site maintainness.
 *
 * @var bool
    */
const Maintenance = false;
```
##### Dynamically 
For update site maintenance dynamically you need to create site admins and create method called adminEnableMaintenance in your Admin controller add following in this method:
```php 
maintenanceInstance()->updataMaintenance(false);
```
### Change the message
For changing the default message or style little bit 
open 503.php from your views folder
**path:** ../App/Views/errors/503.php

## Note:
Once the maintenance is on from configure file it never be off by dynamically process, But if the maintance off from configure file it will be turn on and off by dynamically process.
