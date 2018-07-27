# Libraries
## Benchmarking Class
Zest has a Benchmarking class , enabling the time difference between any two marked points to be calculated.
### Using the Benchmark Class
The Benchmark class can be used within your controllers, views, or your models. The process for usage is this:

- Mark a start point

- Mark an end point

- Run the “elapsed time” function to view the results

   Here’s an example using real code: 

  `$benchmark = new Benchmark;
    $start = $benchmark->start();
   for ($i=0; $i < 1000; $i++) { 
  	$a = $i;
  }
  $end = $benchmark->end();
  echo $benchmark->elapsedTime();`
passed round value if you want round it with 4 int or whatever you like.

## Class Reference
### synopsis
    `
    public function start( void )
    public function end( void )
    public function elapsedTime(int $round = null)
    `