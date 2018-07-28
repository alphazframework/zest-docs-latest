# Upgrade to 1.9.1

## Upgrade core file
you can upgrade core file by running command
`composer update`
this command will automatically upgrade core file of zest framework

## Upgrade zest file
For updraging working file you need replace following files
- Replace Config.php *path:* **projectroot/Config/Config.php**
- Replace system.php *path:* **projectroot/system.php**
- Add `$router->cacheRouters();` Above `$router->dispatch($_SERVER['QUERY_STRING']);` in your routes.php
