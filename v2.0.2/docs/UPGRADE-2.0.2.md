# Upgrade to 2.0.2

## Upgrade core file
You can upgrade core files by running the command:
`composer update`
This command will automatically upgrade the core files of Zest framework.

## Upgrade Zest files

Upgrading the Zest file to 2.0.1 is little difficult. You need to perform following steps.

- First you need to replace config files https://github.com/Softhub99/Zest/tree/2.0.2/Config
  - Config
    - (replace) Database.php
    - (add) Dependencies.php

- Update these files according to your application requirement
- Change folder name ``` App/local``` to ``` App/Local```
- Change folder name ```public``` to ```Public```
- Change folder name ```routes``` to ```Routes```
- Change file name ```routes.php``` to ```Routes.php``` inside ```Routes``` folder
- Update ```system.php``` with https://github.com/Softhub99/Zest/blob/2.0.2/system.php for code optimization
- Congrulation you have successfully upgrade to version 2.0.2


## What's new in this update

- Add Dependency Injection
- Add Logger
- Update Auth system (docs will be uploaded soon)
- Update site.php fix several bugs
- Update helpers.php fix bugs
- Update password Manipulation class

# Note:
The usage of auth and these will be uploaded soon.
