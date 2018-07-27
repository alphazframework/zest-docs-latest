For using twig templating engine with Zest framework you have to download required file run this
`composer require twig/twig`
its download required file 
As everybody know we dont need touch core files so in this case we create theme or whatever you call model
it look like that
we are actually creating `App/Models/Theme.php`
_**App/Models/Theme.php**_

    <?php
	namespace App\Models;
	class Theme{
	    /**
	     * Render a view template using Twig
	     *
	     * @param string $template  The template file
	     * @param array $args  Associative array of data to display in the view (optional)
	     *
	     * @return void
	     */
	    public static function renderTheme($template, $args = [])
	    {
	        static $twig = null;
	        if ($twig === null) {
	            $loader = new \Twig_Loader_Filesystem(dirname(__DIR__) . '/Views');
	            $twig = new \Twig_Environment($loader);
	        }
	        echo $twig->render($template, $args);
	    }
	}

As you see we successfully created our `theme` model now we have to use and create view
Its look like that

      \App\Models\Theme::renderTheme('Home/home.html');

Now we creating our home controller `App/Controllers/Home.php`
_**App/Controllers/Home.php**_

	<?php
	namespace App\Controllers;
	class Home extends \Softhub99\Zest_Framework\Controller\Controller
	{
	    public function index()
	    {
	    	 \App\Models\Theme::renderTemplate('Home/home.html');        

	    }
	}

we have done our home controller now we have to create view Goto `App/Views` create `base.html` here
_**""App/Views/base.html""**_

	<!DOCTYPE html>
	<html>
	<head>
	    <meta charset="UTF-8">
	     <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
	    <link rel="stylesheet" type="text/css" href="css/style.css">
	    <title>{% block title %}{% endblock %}</title>
	</head>
	<body>
	    {% block body %}
	    {% endblock %}
	</body>
	</html>

Now create `Home` directory in `Views` create `home.html` here
_**App/Views/Home/home.html**_

	{% extends "base.html" %}

	{% block title %}Home{% endblock %}

	{% block body %}

	    <div class="container">
			<h1 class='text-center'>Zest Framework</h1>
			<p class='text-center'>Start building your app</p>
		</div>

	{% endblock %}


##### Note after reading this you have to understand that you can easily integrate any third-party labs in `Zest` framework

# Note
This docs is not complete for zest framework we will complete soon