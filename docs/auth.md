Auth Management library bundled with Zest Framework

# Auth Management

## Configuration
There is configuration need for using Auth Management library in zest framework 
open - `Config/Auth.php`
```php
/**
    * Auth database table.
    *
    * @var string
    */
const AUTH_DB_TABLE = 'users';
/**
    * Auth database name.
    *
    * @var string
    */
const AUTH_DB_NAME = 'zestweb';
/**
    * Auth default verification link.
    *
    * @var string
    */
const VERIFICATION_LINK = '/account/verify/';
/**
    * Auth default verification link.
    *
    * @var string
    */
const RESET_PASSWORD_LINK = '/account/reset/password';
/**
    * is send email over smtp.
    *
    * @var string
    */
const IS_SMTP = false;
/**
    * is user need to verify email.
    *
    * @var string
    */
const IS_VERIFY_EMAIL = false;
/**
    * sticky password.
    *
    * @var string
    */
const STICKY_PASSWORD = false;
/**
    * Defaults auth errors msgs.
    *
    * @var array
    */
const AUTH_ERRORS = [
    'password_confitm'   => 'Password much be matched',
    'username_not_exist' => 'Sorry, the username does not exists',
    'email_not_exist'    => 'Sorry, the email does not exists',
    'password_match'     => 'Password does not matched',
    'sticky_password'    => 'Password much be greate then 6 much contain lowercase,uppercase and special character',
    'account_verify'     => 'You should verify your account in order to login, another verification is sended to your email addresss',
    'already_login'      => 'Account already loggedin',
    'need_login'         => 'You need login to your account in order to update profile',
    'token'              => 'Invilid request',
];
/**
    * Defaults auth success msgs.
    *
    * @var array
    */
const SUCCESS = [
    'signin'          => 'Login successfully',
    'signup'          => 'Your account has been created successfully',
    'update'          => 'Your account has been updated',
    'update_password' => 'Your password has been updated',
    'verified'        => 'Your account verified login now to enjoy in our services',
    'reset'           => 'Password reset request has been sended to your email',
];
/**
    * Defaults auth email subjects.
    *
    * @var array
    */
const AUTH_SUBJECTS = [
    'need_verify' => 'Account verification required',
    'verified'    => 'Account verified',
    'reset'       => 'Password reset request',
];
/**
    * Defaults auth email bodies.
    *
    * @var array
    */
const AUTH_MAIL_BODIES = [
    'need_verify' => 'Dear :email your account has been created you need verify your account<br><a href=":link">verify my account</a><br>Click above link if you unable to open copy paste below link <br>:link',
    'reset'       => 'Dear :email We recieve password reset request form your account reset your password now<br><a href=":link">reset my password</a><br>Click above link if you unable to open copy paste below link <br>:link',
    'verified'    => 'Dear :email your account verified login now to enjoy in our services',
];
```
Change this configuration according to your requirement.

## Default Database Structure
required fields
- username
- email
- password
- salts
- token
- resetToken (for allow reset password)

## Lets create simple auth app in Zest Framework
### Required routes
```php
// Add the routes
//create url: yoursite.com
$router->get('',"Home@index");
//Account
//create url: yoursite.com/acount/login
$router->get('account/login',"Account@login");
//create url: yoursite.com/acount/login/action
$router->post('account/login/action',"Account@loginProcess");
//create url: yoursite.com/acount/signup
$router->get('account/signup', "Account@signup");
//create url: yoursite.com/acount/signup/action
$router->post('account/signup/action', "Account@signupProcess");
//create url: yoursite.com/acount/logout
$router->get('account/logout', "Account@logout");
//create url: yoursite.com/@username
$router->get('{username:@([a-zA-Z0-9])+}', "Account@profileView");
//create url: yoursite.com/acount/profile/edit
$router->get('account/profile/edit', "Account@profileEdit");
//create url: yoursite.com/acount/update/action
$router->post('account/update/action', "Account@profileUpdate");
//create url: yoursite.com/acount/update/bio/action
$router->post('account/update/bio/action', "Account@profileBioUpdate");
//create url: yoursite.com/acount/update/password/action
$router->post('account/update/password/action', "Account@profilePasswordUpdate");
//create url: yoursite.com/acount/reset
$router->get('account/reset', "Account@reset");
//create url: yoursite.com/acount/reset/action
$router->post('account/reset/action',"Account@resetProcess");
//create url: yoursite.com/acount/reset/password/$token
$router->get('account/reset/password/{token:[A-Za-z0-9]+}', "Account@resetPassword");
//create url: yoursite.com/account/reset/password-password/process
$router->post('account/reset/password-password/process', "Account@resetPasswordProcess");

```
### Required Controller

#### Home Controller

```php

<?php
namespace App\Controllers;
//for using View
use Zest\View\View;
//for using auth management
use Zest\Auth\Auth;
use Zest\Auth\User;
class Home extends \Zest\Controller\Controller
{
    /**
     * Show the index page.
     *
     * @return void
     */
    public function index()
    {
        $user = new User;
        // in Auth user class there is method isLogin to check is user login or not
        if ($user->isLogin()) {
            // in Auth user class there is method loginUser that return the login user array
            $args = $user->loginUser();
            View::View('account/profile',$args[0]);
        } else {
            View::view('account/signup');
        }
    }
}

```

#### Account Controller

```php

<?php

namespace App\Controllers;

//for using View
use Zest\View\View;
//for using auth
use Zest\Auth\Auth;
use Zest\Auth\User;

class Account extends \Zest\Controller\Controller
{
    //check is user is login or not
    public function isLogin() 
    {
        $user = new User;
        // in Auth user class there is method isLogin to check is user login or not
        if ($user->isLogin()) {
            //redirect() is builtin function in zest framework for redirect to another page
            redirect(site_base_url()."account/profile/edit");
        } 
    }
    //User login form
    public function login()
    {
        $this->isLogin();
        //Loading the view form
        View::view("account/login");
    }
    //Process the login request/actuin
    public function loginProcess() 
    {
        $this->isLogin();
        //Getting the user value
        // using builtin input function
        //escape function clean the input for escaping
        $username = escape(input('username'));
        $password = escape(input('password'));
        $auth = new Auth;
        //Call the auth signin method accpet two arguments
        // username and password 
        $auth->signin()->signin($username,$password);
        //check if there is error
        if ($auth->fail()) {
            // if yes, get the error
            $errors = $auth->error()->get();
            //loop throught the error
            foreach ($errors as $error) {
                if (is_array($error)) {
                    foreach ($error as $value) {
                        echo $value."<br>";
                    }
                } else {
                    echo $error."<br>";
                }
            }
        } else {
            //if no error print 1 on screen means true
            echo '1';
        }
    }
    // Signup form
    public function signup()
    {
        $this->isLogin();
        //Load the signup form
        View::view("account/signup");
    } 
    public function signupProcess() 
    {
        $this->isLogin();
        //Getting the user value
        // using builtin input function
        //escape function clean the input for escaping
        $name = escape(input('name'));
        $username = escape(input('username'));
        $email = escape(input('email'));
        $password = escape(input('password'));
        $confirm = escape(input('confirm'));
        $auth = new Auth;
        //Signup method accpet the three required arguments
        // $username,$email and password 
        //Fourth array argument is optional you can provide many fields in fourth argument if want
        $auth->signup()->signup($username,$email,$password,['name' => $name, 'passConfirm' => $confirm,'role' => 'normal','ip' => (new \Zest\UserInfo\UserInfo)->ip()]);
       //check if there is error
        if ($auth->fail()) {
            // if yes, get the error
            $errors = $auth->error()->get();
            //loop throught the error
            foreach ($errors as $error) {
                if (is_array($error)) {
                    foreach ($error as $value) {
                        echo $value."<br>";
                    }
                } else {
                    echo $error."<br>";
                }
            }
        } else {
            // If no error print successfull message
            echo 'Your account has been created login to enjoy in our services';
        }
    }
    // Logout the users
    public function logout() 
    {
        $auth = new Auth;
        // Call the logout method in auth class
        $auth->logout();
        //redirect the user to login page back
        redirect(site_base_url()."account/login");
    }     
    public function profileEdit()
    {
        $user = new User;
        if ($user->isLogin()) {
            $args = $user->loginUser();
            //profile edit form
            View::View('account/profile',$args[0]);
        } else {
            View::view('errors/404');
        }
    }      
    public function profileUpdate()
    {
        $user = new User;
        $error = false;
        $name = escape(input('name'));
        $username = escape(input('username'));
        $email = escape(input('email'));
        //check if username is already exists
        if ($user->isUsername($username)) {
            $error = true;
            echo "Sorry, {$username} username already exists, try another";
        }
        //check if email is already exists
        if ($user->isEmail($email)) {
            $error = true;
            echo "Sorry, {$email} email already exists, try another";
        }        
        if ($error !== true) {
            $auth = new Auth;
            $id = $user->loginUser()[0]['id'];
            //update the user details
            $auth->update()->update(['name'=>$name,'username'=>$username,'email'=>$email],$id);
            if ($auth->fail()) {
                $errors = $auth->error()->get();
                foreach ($errors as $error) {
                    if (is_array($error)) {
                        foreach ($error as $value) {
                            echo $value."<br>";
                        }
                    } else {
                        echo $error."<br>";
                    }
                }
            } else {
                echo 'Your account has been updated successfully';
            }            
        }
    }
    public function profileBioUpdate()
    {
        $user = new User;
        $bio = escape(input('bio'));      
        $auth = new Auth;
        //get id of login user
        $id = $user->loginUser()[0]['id'];
        //update bio of user
        $auth->update()->update(['bio'=>$bio],$id);
        if ($auth->fail()) {
            $errors = $auth->error()->get();
            foreach ($errors as $error) {
                if (is_array($error)) {
                    foreach ($error as $value) {
                        echo $value."<br>";
                    }
                } else {
                    echo $error."<br>";
                }
            }
        } else {
            echo 'Your account bio has been updated successfully';
        }            
    }  
    public function profilePasswordUpdate()
    {
        $user = new User;
        $password = escape(input('password'));   
        $confirm = escape(input('confirm'));      
        $auth = new Auth;
        //get id of login user
        $id = $user->loginUser()[0]['id'];
        //Update the password
        $auth->update()->updatePassword($password,$confirm,$id);
        if ($auth->fail()) {
            $errors = $auth->error()->get();
            foreach ($errors as $error) {
                if (is_array($error)) {
                    foreach ($error as $value) {
                        echo $value."<br>";
                    }
                } else {
                    echo $error."<br>";
                }
            }
        } else {
            echo 'Your account password has been updated successfully';
        }            
    }    
    public function profileView() 
    {
       $username = $this->route_params['username'];
       $username = str_replace("@", '', $username);
       $user = new User;
       if ($user->isUsername($username)) {
            $args = $user->getByWhere('username',$username);
            //profile view
            View::view('account/profileView',$args[0]);
       } else {
            View::view('errors/404');
       } 
    }  
    //Reset password form where user enter his email
    public function reset()
    {
        // Load the reset form
        //Create your form that should email and one buttom
        View::view("account/reset");
    }
    //Reset password process
    public function resetProcess()
    {
        $auth = new Auth;
        // reset the password
        $auth->reset()->reset(input('email'));
        if ($auth->fail()) {
            $errors = $auth->error()->get();
            foreach ($errors as $error) {
                if (is_array($error)) {
                    foreach ($error as $value) {
                        echo $value."<br>";
                    }
                } else {
                    echo $error."<br>";
                }
            }
        } else {
            echo 'Your Password reset request has been recieved check your email';
        }  
    }
    public function resetPassword()
    {
        $token = $this->route_params['token'];
        $user = new User;
        //check if reset token is exists
        if ($user->isResetToken($token)) {
            $args = ['token' => $token];
            View::view("account/reset_password",$args);
        } else {
            View::view("errors/404");
        }
    }
    public function resetPasswordProcess()
    {
        $password = input('password');
        $confirm =  input('confirm');
        $token = input('token');
        $user = new User;
        //get the user id by resetToken
        $id = $user->getByWhere('resetToken',$token)[0]['id'];
        $auth = new Auth;
        //update the user password
        $auth->update()->updatePassword($password,$confirm,$id);
        if ($auth->fail()) {
            $errors = $auth->error()->get();
            foreach ($errors as $error) {
                if (is_array($error)) {
                    foreach ($error as $value) {
                        echo $value."<br>";
                    }
                } else {
                    echo $error."<br>";
                }
            }
        } else {
            $auth->update()->update(['resetToken' => 'NULL'],$id);
            echo "Password update successfully ";
        }         
    }
}

```

In the account controller we called method form auth management 

### View

Create view yourself or download files form here
https://github.com/Lablnet/Zest-Auth-App/tree/master/App/Views
and download required css/js or image files form here
https://github.com/Lablnet/Zest-Auth-App/tree/master/Public
the folder structure should be same.

## Source code
The source code of this available in github feel free to download and contribute
https://github.com/Lablnet/Zest-Auth-App
