Zest framework provides two ways for views. The default, built-in templating
engine, and without a templating engine. Zest framework can't support
third-party templating engines, but if you want to, you can see how to
implement third-party templating engines in next section.

# Creating a View in simple way without a templating engine.
Typically, all views should be created inside the `App/Views/` folder. Suppose
you're going to create a home view. So in this case, save the file as
`App/Views/Home.php` or `App/Views/Home/Home.php` (whatever you want).

```HTML
	<!doctype html>
	<body>
		<div class="container">
			Welcome
		</div>
	</body>
```

You can access the view form controller by `echo View::View("Home/index");`.

Your home controller should look like this:

```PHP
<?php
namespace App\Controllers;
use \Softhub99\Zest_Framework\View\View;

class Home extends \Softhub99\Zest_Framework\Controller\Controller
{
    public function index()
    {
        echo View::view("Home/index");
    }
}
```

In the case of passing parameter, it should look like this:

```PHP
$data = ['name' => 'malik'];
echo View::View("Home/index",$data);
```

You can access this parameter by:

```PHP
$name = $args['name'];
```

# Creating a View in a simple way with a templating engine
Zest supports a built-in template engine that you can use in simple way.

```PHP
        echo View::randerTemplate("Home/template.php",[
        		'name' => "malik",
        ]);
```

Use in view file like this:

```PHP
		{% name %}
```

It prints "malik" on the screen.


# Minify HTML files
ZestFramework minifies HTML by default. If you don't want to minify HTML view files, you should passed `false` argument in view method of the View class

 - **First Argument:** file name with path like file or path/file.
 - **Second Argument:** Any parameter that you want to be passed must be in an array.
 - **Third Argument:** Minify; `true` => Minify, `false` => Don't minify. Must be `bool`. Default value is `true`.
