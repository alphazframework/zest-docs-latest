_The controller is generally responsible for performing a request action._
# Creating a Controller
You can easily create controllers in ""Zest"" Framework goto _App/Controllers/_ form project root you have to create more controller here.
## Writing simple controller

```php		
<?php
namespace App\Controllers;
	use Zest\View\View; //you will learn more about view in later this is for accessing view
class Home extends \Zest\Controller\Controller
{

	public function index()
	{

		echo View::view("Home/index"); //you will learn more about view in later this is for accessing view

	}

}
```

This is easy way for creating controllers this create home page

# Complex way for writing controller

```PHP
	<?php

	namespace App\Controllers;

	use Zest\View\View; //you will learn more about view in later this is for accessing view

	class About extends \Zest\Controller\Controller
	{

	    public function index()
	    {
	       echo $this->route_params['username']; //$this->router_params use for accessing paramter begin passed for more information see https://github.com/Softhub99/Zest/wiki/Routing#router-with-complex-parameter
	    }
	    public function about()
	    {
	        echo view::SetTemplate("Home/index.html",[
	    'header' => 'PHP Template engine',]); //you will learn more about view/template engine in later this is for accessing view
	    }

	}
```
