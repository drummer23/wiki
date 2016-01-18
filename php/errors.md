#Error Handling

##Error Types

- Compile-time errors*
- Fatal Errors*
- Recoverable errors
- Warnings
- Notices

*cannot be trapped

##Configuration

globaly in php.ini or dynamically within script

```
error_repporting=E_ALL & ~E_NOTICE
display_errors=on
log_errors=on
```
Use set_error_handler to set custom error handler

##Stack Traces

are presented inside->out
first entry is where the exception happened. last entry is where the code finaly abortet

##Handling

```php

try {
	throw new Exception('Something happene');
} catch (Exception $e) {
	echo 'Caught Exception' : ’ . $e->getMessage();
}

```