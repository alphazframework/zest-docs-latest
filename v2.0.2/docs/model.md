# Model
Model are actually behavior of app.

# Creating the model
You will find model directory in `App/Models/`, All the models store here
Suppose you want create database modal thats handel database stuff
it will look like that

```PHP
<?php
namespace App\Models;
use Zest\Database\Zest\Builder as Model;
class Post extends Model
{
    public function get()
    {
    	$db = new Mode;
        $db->method(); //example code
    }
}
```

# Accessing models in Controllers
You can accesss models in following way
`\App\Models\modalname::method(param);`
So in our above example its look like
`\App\Models\Post::yourmethod`
