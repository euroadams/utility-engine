# Utility Engine
A PHP utility class for managing varieties of simple and complex tasks

> [!CAUTION]
> All example codes herein are strictly for illustration purposes only. It's recommended to optimize before using for production.

## Instantiating the Class :

The utility `Engine` can be instantiated using the standard PHP syntax as follows

```php

<?php

$ENGINE = new Engine();

?>

```

## Features & Usage Guide :

### 1. Text Masking or Cloaking
To use this feature, simple call the `cloak()` method with the necessary parameters as shown below 

**`cloak()` Method Paramaters** :

```php

<?php

//Parameter Definition

$ENGINE->cloak($data, $cloakPercent=60, $maskLen=0, $cipherSym='x');

/****
 *  @param $data => The text you wish to mask/cloak
 * 
 *  @param $cloakPercent => The portion of the text you wish to mask/cloak expressed in percentage
 *  => defaults to 60
 * 
 *  @param $maskLen => The length of the character you wish to use for the text mask/cloak
 *  => defaults to 0, which means that the number of characters to be masked is replaced exactly with
 *  corresponding cypher length
 * 
 *  @param $cipherSym => The character you wish to use for the text mask/cloak
 *  => defaults to x
 ****/        

?>

```

**Left Hand Side (LHS) Masking/Cloaking** :
This is the default masking direction. The specified portion of the text is cloaked from the left hand side

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40);

/****
 * 
 * INPUT TEXT : utility.engine.test@gmail.com
 * 
 * OUTPUT TEXT : xxxxxxxxxxxxne.test@gmail.com
 *  
****/        

?>

```


**Right Hand Side (RHS) Masking/Cloaking** :
To to change the masking direction, prepend negative sign `-` to the `$maskLen` parameter. This will force specified portion of the text to be cloaked from the right hand side

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40, '-0');

/****
 * 
 * INPUT TEXT : utility.engine.test@gmail.com
 * 
 * OUTPUT TEXT : utility.engine.texxxxxxxxxxxx
 *  
****/        

?>

```

**Change Masking/Cloaking Cipher** :
To to change the masking cipher, we simply pass the desired masking character to the `$cipherSys` parameter

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40, 0, '*');

/****
 * 
 * INPUT TEXT : utility.engine.test@gmail.com
 * 
 * OUTPUT TEXT : ************ne.test@gmail.com 
 *     
****/        

?>

```

**Change Masking/Cloaking Cipher Length** :
To to change the masking cipher length, we simply pass the desired length to the `$maskLen` parameter

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40, 2);

/****
 * 
 * INPUT TEXT : utility.engine.test@gmail.com
 * 
 * OUTPUT TEXT : xxne.test@gmail.com
 * 
****/        

?>

```


###  2. Number Formating :
This feature helps you to format numbers into comma separated thousands and deecimal places. It also allows the use of `K`, `M`, `B`,  and `T` to format the number into thousands, millions, billions, and trillions 

```php

<?php

//Parameter Definition

$ENGINE->format_number($num, $dcp=0, $kfmt=true);

/****
 *  @param $num => The number you wish to format
 * 
 *  @param $dcp => The number of the decimal places you desire
 *  => defaults to 0 (no decimal places)
 * 
 *  @param $kfmt => A boolean that specify whether to use K, M, B, T format 
 *  => defaults to true 
 * 
 ****/        

?>

```

**Formating Using Comma Separated Thousands** :
```php

<?php
    
$ENGINE->format_number(295000000, 0, false);

/****
 * 
 * INPUT NUMBER : 295000000
 * 
 * OUTPUT NUMBER : 295,000,000 
 * 
****/        

?>

```

**Formating Using Comma Separated Thousands With Decimal Places** :
```php

<?php
    
$ENGINE->format_number(295000000, 4, false);

/****
 * 
 * INPUT NUMBER : 295000000
 * 
 * OUTPUT NUMBER : 295,000,000.0000 
 * 
****/        

?>

```

**Formating Using K, M, B, T** :
```php

<?php
    
$ENGINE->format_number(295000000);

/****
 * 
 * INPUT NUMBER : 295000000
 * 
 * OUTPUT NUMBER : 295M 
 * 
****/        

?>

```

###  3. MORE DOCUMENTATION LOADING SOON :