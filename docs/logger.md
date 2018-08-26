Logger library bundled with Zest Framework

# Logger
Logging is one of the most ubiquitous tasks encountered in PHP. We use logs to track error messages, record important events, and debug problems with the code.

## Use logger

```php 
$logger = new \Zest\Common\Logger\Logger;
$logger->notice('This file {file} is not found',['file' => 'user.jpg']);
//Display the log msg
// var_dump($logger->get);
echo $logger->get()['message'];
//echo View::view('Home/index');
```
the `get()` method return array , level and message

## Log file
Log file is locate in `Storage/Data/.logs`

## Levels
- emergency => ```$logger->emergency(msg,[context])```
- alert => ```$logger->alert(msg,[context])```
- critical => ```$logger->emergency(msg,[critical])```
- error => ```$logger->error(msg,[context])```
- warning => ```$logger->warning(msg,[context])```
- notice => ```$logger->notice(msg,[context])```
- info => ```$logger->info(msg,[context])```
- debug => ```$logger->debug(msg,[context])```

