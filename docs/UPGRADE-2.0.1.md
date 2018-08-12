# Upgrade to 2.0.1

## Upgrade core file
You can upgrade core files by running the command:
`composer update`
This command will automatically upgrade the core files of Zest framework.

## Upgrade Zest files

Upgrade the Zest file to 2.0.1 is little hard 
you need perform following steps

- first you need to replace configs files
  - Config
    - Auth.php   
    - Config.php   
    - Database.php   
    - Email.php   

- Update according to your application requirement
- Now download notepad++ as its easy to use open the notepad++ 
- Click `Search` form menu then click `Find in files`
- Write `Softhub99\Zest_Framework` in *find what* box, and write `Zest` in *Replace With* box
- Browse your project from directory box
- Now click *Replace in files*
- Congrulation you have successfully upgrade to version 2.0.1


## What's new in this update

- Added Auth library
- Change name space
- Update cookies class fix several bugs
- Added password manipulation class
- Update database management system
- Update Mail class fix bug
- further improvement

# Note:
The usage of auth will be uploaded soon.