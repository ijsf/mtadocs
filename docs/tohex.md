This function converts a decimal number to a hexadecimal number.
\* **NOTE:** This is made to be used clientside! Use string.format ( "%X", num ) to convert a number to hex serverside, since this does not work properly clientside.

Syntax
------

``` lua
string toHex( int number )
```

### Required Arguments

-   **number**: The number to be converted.

### Returns

Returns a string containing the Hex value.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function toHex ( n )
    local hexnums = {"0","1","2","3","4","5","6","7",
                     "8","9","A","B","C","D","E","F"}
    local str,r = "",n%16
    if n-r == 0 then str = hexnums[r+1]
    else str = toHex((n-r)/16)..hexnums[r+1] end
    return str
end
```

</section>
Example
-------

This example outputs the hexadecimal number in a string. (“1F5F79A0”)

``` lua
print ( toHex ( tonumber ( 0x1F5F79A0 ) ) )
```

Author: Remi-X

See Also
--------
