Zest provides different methods to easily validate data.

## Validation simple usage

Let's consider a simple example. We shall attempt to accept input from the user. The first thing we need to do is define the necessary routes.

### Define Route

```PHP

$router->add('user/create',['controller'=>"User",'action'=>'userCreate']);

```

### Create a Controller with Validation Logic

```PHP

<?php
namespace App\Controllers;
use Softhub99\Zest_Framework\View\View;
use Softhub99\Zest_Framework\Validation\Validation;

class User extends \Softhub99\Zest_Framework\Controller\Controller
{

    public function usercreate()
    {
        if (input('submit')) {
            $rules = [
                'username' => ['required' => true, ],
                'email' => ['required' => true],
                'password' => ['required' => true, ],
            ];
            $validation = new Validation(input_all(),$rules,'input');
            if($validation->fail()){
                $errors = $validation->error()->get();

                foreach ($errors as $error) {
                    foreach ($error as $value) {
                        echo $value."<br>";
                    }
                }
            } else {
                //TO-Do create the user
                //We will provide auth clas soon
            }
        } else {
            View::view('Home/form');
        }
    }
}

```
#### User form file

```HTML

<!DOCTYPE html>
<html>
<head>
	<title>Signup</title>
</head>
<body>
	<form actio='' method='post'>
		<label>Name: </label>
		<input type="text" name="username" ><br>
		<label>Email: </label>
		<input type="text" name="email" ><br>
		<label>Password: </label>
		<input type="text" name="password" ><br>
		<input type="submit" name="submit">
	</form>
</body>
</html>
```

### Getting validation errors for specific fields


```PHP
 /**
     * Check if a given key exists in error message
     *
     * @param $key
     * @return bool
 */

 $exists = $validator->error()->has('username');


 /**
    *  Get all the validation errors for a specific fields
 *
    *  @param $key
    *  @return array
 */

$passwordErrors = $validator->error()->get('password');

/**
    * Get the first validation error for a specific fields
 *
    * @param $key
    * @return mixed
 */

$firstError = $validator->error()->first('email');
//OR
$lastError = $validator->error()->lase('email');
}

```
# Available Validation Rules
The following validation rule are available starting from Zest v1.9.1

## Required rule
The required rule is used to specify that a specific field cannot be empty:

```php
    $rules = [
        'username' => ['required' => true,],
    ];
```
## Int rule
The int rule is used to specify that a specific field much be int:

```php
    $rules = [
        'favNum' => ['int' => true,],
    ];
```
## Float rule
The float rule is used to specify that a specific field much be float:

```php
    $rules = [
        'payment' => ['float' => true,],
    ];
```
## String rule
The string rule is used to specify that a specific field much be string:

```php
    $rules = [
        'name' => ['string' => true,],
    ];
```
## Email rule
The required rule is used to specify that a specific field must be a valid email address:

```php
    $rules = [
        'email' => ['email' => true,],
    ];
```
## IP rule
The IP rule is used to specify that a specific field must be valid IP address:

```php
    $rules = [
        'email' => ['email' => true,],
    ];
```
## JSON rule
The JSON rule validates the json value

```php
    $validation = new Validation('jsonValue','validate','json');
```
## Unique rule
The unique rule allows you to check if a given value exists in a specific database table:
```php
    $validation = new Validation(['field'=> 'fieldLike_username','value'=>'valueToBeSearch'],'tabelName');
```
