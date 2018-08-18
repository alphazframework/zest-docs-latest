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
