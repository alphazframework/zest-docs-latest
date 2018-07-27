# Where to Define Your Application Routes
**_goto routes directory of project you will see routes.php all routes define here_**

## Simple way to define router
`$router->add('path', ['controller' => 'name', 'action' => 'name']);`

the path is the like example.com/about in this case about will be the path controller is the name of controller which one you want use for this route action is method of controller

### Dispatch
`$router->dispatch($_SERVER['QUERY_STRING']);` are use to process request
# Route with Closure or Callback
You can also define a route that uses a Closure or callback as the handler like so
 `$router->add('user/{id:[0-9]}',  function ($args) {
    echo 'Example route using closure '.$args['id'] . " ".$args['name'];
  });`

## Router with parameter
Router with parameter means you want passing parameter to the url e.g example.com/profile/100 `100` is the parameter of the request
`$router->add('{controller}/{id:\d+}/{action}', ['controller' => 'profile','action' => 'index']);`
This will create example.com/profile/100 for you you can access by placeholder that you use in case `id`

## Router with complex parameter
You can also add router with complex parameter in this case you have to use `regx`
`$router->add('{controller}/{username:[a-z+0-9]+}/{action}', ['controller' => 'profile','action' => 'index']);`
its create url example.com/profile/username you can pass string+numbers here and access through placeholder that you define in this case `username`