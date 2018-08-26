# Upgrade FROM 2.0.2

## Upgrade core file
You can upgrade core files by running the command:
`composer update`
This command will automatically upgrade the core files of Zest framework.

## Upgrade Zest files

Upgrading the Zest file to 2.0.3 is easy

- You need to replace config files https://github.com/Softhub99/Zest/tree/2.0.3/Config
  - Config
    - (replace) Database.php
    - (replace) Dependencies.php


- Congrulation you have successfully upgrade to version 2.0.3


## What's new in this update

- Supports for RESTs routes in router class and components
- Update Dependency Injection
- Update Mysql class (remove extra comments)
- Update files class (add : 'application/x-zip-compressed' mine type)
- Update validation class (fix issue undefine constant)
- Update auth -signin class fix issue sending verifcation email again & again
- Update input class (fix typo)
- Update helpers.php fix bugs (add function restore_line_break())
- Add addRoutes method in router class and in component for adding multiple routers at a time
- Adding supports Controller@method in routes


