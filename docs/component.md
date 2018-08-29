# Component

Zest Framework supports a component system/feature.

## What is a component?

A component is a piece of code that has its own routes, controllers, models, views, middleware and locals.

## The structure of components
The structure of components is as follows.
All components should be in `App/Components` folder

In this example we're going to create helloworld component. The structure is as follow.

- Components {main component folder}
  - helloworld {sub component folder e.g component name}
    - Controllers {folder contains controllers of component}
    - local {folder contains language files of component}
    - Models {folder contains models of component}
    - Middleware {folder contains middleware of component}
    - Views {folder contains views of component}
    - routes.php  {file, where the routes are defined}

Let's create a `helloworld` component.

First, add our route in `routes.php`

```php
<?php

// namespace is required to define your component so that you can add many routes into one component as well.
$namespace = "App\Components\helloworld\Controllers";

// This creates the url `localhost/blog/helloworld`.
$com->add('helloworld', ['controller' => 'Home', 'action' => 'index', 'namespace'=>$namespace]);

// the helloworld is the component name if you have different component chagne it according to name.
```
Now create our `Home.php` in controllers folder

```php

<?php

namespace App\Components\hello\Controllers;

use Zest\Component\View\View;

class Home extends \Zest\Component\Controller\Controller
{
    /**
     * Show the index page.
     *
     * @return void
     */
    public function index()
    {
        //prototype View::view('componentName','View files',$args array (optional));
        echo View::view('helloworld', 'Home/index');
        //again the word helloworld is our component name
    }
}

```

Then write `index.php` in the Views/Home folder

```html
<!doctype html>
<html lang="<?= lang(); ?>">
	<head>
		  <meta charset="utf-8">
 		  <meta name="viewport" content="width=device-width, initial-scale=1">
 		  <link rel="shortcut icon" type="image/png" href="<?= site_base_url(); ?>/image/logo.png"/>
          <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.0/css/bootstrap.min.css">
          <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
          <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.0/umd/popper.min.js"></script>
          <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.0/js/bootstrap.min.js"></script>
   		 <link rel="stylesheet" type="text/css" href="<?= site_base_url(); ?>/css/style.css">
		<title><?= printl('title:home'); ?></title>
	</head>

<body>
	<div class='container-fluid'>
		<h1><?= printc('title:home:hello'); ?></h1>
	</div>
</body>
</html>

```
`printc()` is a built-in function in Zest framework for printing language strings in components.
`site_base_url()` returns the current URL of the site.

Now lastly, create our language file `en.php` in the local folder.

```php
<?php

 return [
    'title:home:hello' => 'Hello World',
];

```

Congratulations! You have successfully created a component.
