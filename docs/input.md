Input Handling library bundled with Zest Framework

# Input Handling
Input handling is the way getting input form users (which is also called form submittion)

## input function
input function is use to get any http type value its accpet one paramter which is name of field

```php
  $username = input('username');
```

## Escape function

The escape function is use to clean user input form any type of malicious code its accpet one paramter which is value that you want clean

```php
$username = input('username');
$username = escape($username);
//OR
$name = escape(imput('name'));

```
