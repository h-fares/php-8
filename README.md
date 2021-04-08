# The new PHP-8

In the new version of PHP so many features have been added and upgraded, let's see them togather.


## Named arguments
Now we can pass all arguments with there name to any function.
#### PHP-7
```php
anyFunction($name, $age=18, $city="london") {}
// The way to call this function is:
$this->anyFunction('Name', 20)

// The value 20 will be assigned for $age
```
#### PHP-8
```php
anyFunction($name, $age=18, $city="london") {}
// The new way to call this function is:
$this->anyFunction('Name', city:'Berlin')

// PHP will understand that the second argument is assigned for city and $age will still as deffined
```

