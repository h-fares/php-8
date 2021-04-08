# The new PHP-8

In the new version of PHP so many features have been added and upgraded, let's see them togather.


## Named arguments
Now we can pass all arguments with there name to any function.
#### PHP-7
```php
function anyFunction($name, $age=18, $city="london") {}
// The way to call this function is:
$this->anyFunction('Name', 20)

// The value 20 will be assigned for $age
```
#### PHP-8
```php
function anyFunction($name, $age=18, $city="london") {}
// The new way to call this function is:
$this->anyFunction('Name', city:'Berlin')

// PHP will understand that the second argument is assigned for city and $age will still as deffined
```
Source: [php-8/named-arguments](https://www.php.net/releases/8.0/en.php#named-arguments)


## Attributes
Instead of PHPDoc annotations to document a function, you can now use structured metadata with PHP's native syntax. 

#### PHP-7
```php
class anyClass {
  /**
   * @Route("/api/things/{name}", methods={"GET"})
  */
  
  function anyFunction($name) {}
}
```

#### PHP-8
```php
class anyClass {

  #[Route("/api/posts/{id}", methods: ["GET"])]
  
  function anyFunction($name) {}
}
```
Source: [php-8/attributes](https://www.php.net/releases/8.0/en.php#attributes)


## Constructor property promotion
Usually to initialize a class and assign a value to all porperties, you have to deffine all properties and give the a value in the constructre. 
Like in PHP-7
#### PHP-7
```php
class anyClass {
  private $prop1;
  private $prop2;
  
  public function __construct($temp1 = 0, $temp2 = 0) {
    $this->prop1 = $temp1;
    $this->prop2 = $temp2;
  }
}
```
In PHP-8 now it is simple to initialize a class and assign a value to property

#### PHP-8
```php
class anyClass {
 
  public function __construct(
    private $prop1 = 0, 
    private $prop2 = 0) {}
}
```
Source: [php-8/constructor-property-promotion](https://www.php.net/releases/8.0/en.php#constructor-property-promotion)


## Union types
In PHP you do not have to deffine a type of an attribute, but you can wherever you want change the type of an attribute.

#### PHP-7

```php
$number = 3; // It is type int

$new_number = (string)$number; // It is type string, and it is right in PHP-7. Although you want to assign just number in the $number.
```

#### PHP-8
```php
int|float $number = 3; // It is type int

$new_number = (string)$number; // Wrong and gives error
```
Source: [php-8/union-types](https://www.php.net/releases/8.0/en.php#union-types)

## Match expression
A new expression *"match"*, similer to switch but in simpler way.

#### PHP-7
```php
switch (5) {
  case '5':
    $result = "Wrong";
    break;
  case 5:
    $result = "Right";
    break;
}
echo $result;
```

#### PHP-8
```php
$result = match (5) {
  '5' => "Wrong",
   5 => "Right",
};
#echo $result;
```

The highlight here is: you can direct assign the expression to an attribute.
Source: [php-8/match-expression](https://www.php.net/releases/8.0/en.php#match-expression)

## Nullsafe operator
In PHP if you tried to get an attribut of a null object you will get an error
