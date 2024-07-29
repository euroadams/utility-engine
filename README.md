# Utility Engine
A PHP utility class for managing varieties of simple and complex tasks


## Usage Guide :

> [!CAUTION]
> All example code here in are strictly for illustration purpose only. It's recommended to optimize before using in production.

## Instantiating the Engine :

An instance of the utility engine can be instantiated using the standard PHP syntax as follows

```php

    <?php

        $ENGINE = new Engine();
    
    ?>

```

## Features :

1. ### Text Masking or Cloaking
To use this feature, simple call the `cloak()` method with the necessary parameters as shown below 

```php

    <?php

        //Parameter Definition

        $ENGINE->cloak($data, $cloakPercent=60, $maskLen=0, $cipherSym='x');

        /****
         *  @param $data => The text you wish to mask/cloak
         * 
         *  @param $cloakPercent => The portion of the text you wish to mask/cloak expressed in percentage
         *  defaults to `60`
         * 
         *  @param $maskLen => The length of the character you wish to use for the text mask/cloak
         *  defaults to `0` which means that the number of characters to be masked is replaced exactly with
         *  corresponding cypher length
         * 
         *  @param $cipherSym => The character you wish to use for the text mask/cloak
         *  defaults to `x`
         ****/        
    
    ?>

```

### Left Hand Side (LHS) Masking/Cloaking :
This is the default masking direction. The specified portion of the text is cloaked from the left hand side

```php

    <?php
        
        $ENGINE->cloak("UTILITY ENGINE TEXT MASK TEST");

        /****
         * 
         * INPUT TEXT : `UTILITY ENGINE TEXT MASK TEST`
         * 
         * OUTPUT TEXT : `xxxxxxxxxxxxxxxxxXT MASK TEST`
         
         ****/        
    
    ?>

```


### Right Hand Side (RHS) Masking/Cloaking :
To to change the masking direction, prepend negative sign `-` to the `$maskLen` parameter. This will force specified portion of the text to be cloaked from the right hand side

```php

    <?php
        
        $ENGINE->cloak("UTILITY ENGINE TEXT MASK TEST", 60, '-0');

        /****
         * 
         * INPUT TEXT : `UTILITY ENGINE TEXT MASK TEST`
         * 
         * OUTPUT TEXT : `UTILITY ENGIxxxxxxxxxxxxxxxxx`
         
         ****/        
    
    ?>

```

### Change Masking/Cloaking Cipher :
To to change the masking cpher, we simply pass the desired masking character to the `$cipherSys` parameter

```php

    <?php
        
        $ENGINE->cloak("UTILITY ENGINE TEXT MASK TEST", 60, 0, '*');

        /****
         * 
         * INPUT TEXT : `UTILITY ENGINE TEXT MASK TEST`
         * 
         * OUTPUT TEXT : `*****************XT MASK TEST`
         
         ****/        
    
    ?>

```

2. ### 