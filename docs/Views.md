Zest framework provide two way for views default built-in templating engine and without templating  engine, Zest framework cant support third-party templating engine but you can implement if you want you can see how to implement third-party templating engine in next section.
# Creating a View in simple way without templating engine
Typically all views should be created inside `App/Views/` folder, 
suppose you are going to create home view so in this case Save file `App/Views/Home.php` or `App/Views/Home/Home.php` what ever you want

	<!doctype html>
	<body>
		<div class="container">
			Welcome
		</div>
	</body>	

You can access the view form controller by ` echo View::View("Home/index");`
Your home controller look like that

     <?php
	namespace App\Controllers;
	use \Softhub99\Zest_Framework\View\View;

	class Home extends 
	\Softhub99\Zest_Framework\Controller\Controller
	{

	    public function index()
	    {
	        echo View::view("Home/index");        

	    }
	}

In case passing parameter you its look like

        $data = ['name' => 'malik'];
        echo View::View("Home/index",$data);

You can access this parameter by 

	$name = $args['name'];


# Creating a View in simple way with templating engine
Zest support built-in tamplet engine
you can use in simple way

        echo View::randerTemplate("Home/tamplet.php",[
        		'name' => "malik",
        ]);

Use in view file like that

		{% name %}

its print malik on screen


# Minify HTML files
ZestFramework minify html by default if you didnt want minify html view files you should passed false argument in view method of View class

 - **First Argument:** file name with path like file or path/file
 - **Second Argument:** Any parameter that you want to passed much be in array
 - **Third Argument:** Minify , true=> minify , false => not minify much be bool , default value is true


