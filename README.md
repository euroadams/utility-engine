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
To use this feature, simply call the `cloak()` method with the necessary parameters as shown below 

:point_right: **`cloak()` Method Paramaters** :

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
:point_right: **Left Hand Side (LHS) Masking/Cloaking** :
This is the default masking direction. The specified portion of the text is cloaked from the left hand side

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40);

/****
 * 
 * OUTPUT:
 * 
 * utility.engine.test@gmail.com => xxxxxxxxxxxxne.test@gmail.com 
 *  
****/        

?>

```


:point_right: **Right Hand Side (RHS) Masking/Cloaking** :
To change the masking direction, prepend negative sign `-` to the `$maskLen` parameter. This will force specified portion of the text to be cloaked from the right hand side

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40, '-0');

/****
 * 
 * OUTPUT:
 * 
 * utility.engine.test@gmail.com => utility.engine.texxxxxxxxxxxx 
 *  
****/        

?>

```

:point_right: **Midpoint Masking/Cloaking** :
To change the masking direction to the middle, prepend dot sign `.` to the `$maskLen` parameter. This will force specified portion of the text to be cloaked from the midpoint and span evenly to the sides

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40, '.0');

/****
 * 
 * OUTPUT:
 * 
 * utility.engine.test@gmail.com => utility.xxxxxxxxxxxxxmail.com
 *  
****/        

?>

```

:point_right: **String Index Masking/Cloaking** :
To cloak any portion of the text that is of interest to you, simply pass a comma-separated `start` and `stop` index as parameter to the `$cloakPercent` and prepend a pipe sign `|` to it as shown below. 
This will cloak the portion of the text specified by the `start` and `stop` index accordingly. 

To reverse the count direction to the end of the text, simply prepend negative sign `-` to the `start` index as seen illustarted below.

> [!NOTE]
> The `start` and `stop` index follows standard `PHP` string indexing style.
`0` marks the first character for positive indexing and `-1` for negative indexing

```php

<?php

//Cloak Only the 'engine' part in the text
$ENGINE->cloak("utility.engine.test@gmail.com", '|8,6');

/****
 * 
 * OUTPUT:
 * 
 * utility.engine.test@gmail.com => utility.xxxxxx.test@gmail.com
 *  
****/  


//Cloak Only the 'engine' part in the text while counting from the end
$ENGINE->cloak("utility.engine.test@gmail.com", '|-21,6');

/****
 * 
 * OUTPUT:
 * 
 * utility.engine.test@gmail.com => utility.xxxxxx.test@gmail.com
 *  
****/

?>

```



:point_right: **Change Masking/Cloaking Cipher** :
To change the masking cipher, we simply pass the desired masking character to the `$cipher` parameter

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40, 0, '*');

/****
 * 
 * OUTPUT:
 * 
 * utility.engine.test@gmail.com => ************ne.test@gmail.com 
 *     
****/        

?>

```

:point_right: **Change Masking/Cloaking Cipher Length** :
To change the masking cipher length, we simply pass the desired length to the `$maskLen` parameter

```php

<?php
    
$ENGINE->cloak("utility.engine.test@gmail.com", 40, 2);

/****
 * 
 * OUTPUT:
 * 
 * utility.engine.test@gmail.com => xxne.test@gmail.com
 * 
****/        

?>

```


###  2. Number Formatting :
This feature helps you to format numbers into comma separated thousands and deecimal places. It also allows the use of `K`, `M`, `B`,  and `T` to format the number into thousands, millions, billions, and trillions respectively

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

:point_right: **Comma Separated Format** :
```php

<?php
    
$ENGINE->format_number(295000000, 0, false);

/****
 * 
 * OUTPUT:
 * 
 * 295000000 => 295,000,000
 * 
****/        

?>

```

:point_right: **Comma Separated Format With Decimal Places** :
```php

<?php
    
$ENGINE->format_number(295000000, 4, false);

/****
 * 
 * OUTPUT:
 * 
 * 295000000 => 295,000,000.0000 
  
 * 
****/        

?>

```

:point_right: **K, M, B, T Format** :
```php

<?php
    
$ENGINE->format_number(2500);
$ENGINE->format_number(295000000);
$ENGINE->format_number(295000000000);
$ENGINE->format_number(295000000000000);

/****
 * 
 * OUTPUT:
 * 
 * 2500 => 2.5K
 * 295000000 => 295M
 * 295000000000 => 295B
 * 295000000000000 => 295T
 * 
****/        

?>

```

###  3. MORE DOCUMENTATION LOADING SOON :
