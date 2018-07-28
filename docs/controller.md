_The controller is generally responsible for performing a request action._
# Creating a Controller
You can easily create controllers in ""Zest"" Framework goto _App/Controllers/_ form project root you have to create more controller here.
## Writing simple controller
	<?php
	namespace App\Controllers;
     use Softhub99\Zest_Framework\View\View; //you will learn more about view in later this is for accessing view
	class Home extends \Softhub99\Zest_Framework\Controller\Controller
	{

	    public function index()
	    {
	    
	        echo View::view("Home/index"); //you will learn more about view in later this is for accessing view

	    }
	   
	}

This is easy way for creating controllers this create home page 

# Complex way for writing controller 


		<?php

		namespace App\Controllers;

		use Softhub99\Zest_Framework\View\View; //you will learn more about view in later this is for accessing view

		class About extends \Softhub99\Zest_Framework\Controller\Controller
		{
		 
		    public function index()
		    {
		       echo $this->route_params['username']; //$this->router_params use for accessing paramter begin passed for more information see https://github.com/Softhub99/Zest/wiki/Routing#router-with-complex-parameter
		    }
		    public function about()
		    {
		        echo view::SetTemplate("Home/index.html",[
		    'header' => 'PHP Tamplet engine',]); //you will learn more about view/tampleting in later this is for accessing view
		    }    
	    
		}


