# Classes

## Definiton

```php

class car
{
    const MYCONSTANT = “some value”;
    private $color;

    public function __construct($color = null) {
    	$this->color = $color;
	}

    public function getColor() {
    	return $this->color;
    }

    public function printConstant() {
    	echo self::MYCONSTANT;
    }
}
```

## Instiation

```php
$golf = new car(‘red’);
```

## Instance of
```php
if ($variable instanceof car)
```
