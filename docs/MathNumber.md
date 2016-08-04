This function can be used to take or add a number from a large number.

MTA clients do only support 24-bits numbers, therefore you can't take or add a single digit from large numbers like '1364576384'.

This function is only needed clientside since the server runs with a floating-point precision of 56-bits, however this works also serverside.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **num**: The number you want to edit
-   **integer**: The amount you want to add or take from the number
-   '''type ''': Can be either '-' or '+'

### Returns

Returns a number if everything went good, *false* otherwise.

Code
----

``` lua
-- Function that takes a digit from a larger number
function mathNumber ( num, integer, type )
    if not ( num ) or not ( integer ) then return false end

    local function formatNumber( numb )
    if not ( numb ) then return false end
        local fn = string.sub( tostring( numb ), ( #tostring( numb ) -6 ) )
        return tonumber( fn )
    end
    
    if not ( type ) or ( type == "+" ) then
        local fn = string.sub( tostring( num ), 1, -8 )..( formatNumber ( num ) ) + integer
        return tonumber( fn )
    else
        local fn = string.sub( tostring( num ), 1, -8 )..( formatNumber ( num ) ) - integer
        return tonumber( fn )
    end
end
```

Example
-------

``` lua
mathNumber ( 1364576384, 1, '-' )
-- Returns: 1364576383

1364576384 - 1
-- Returns: 1364576384

mathNumber ( 1364576384, 1, '+' )
-- Returns: 1364576385

1364576384 + 1
-- Returns: 1364576384
```

Author: DennisUniOn

See Also
--------
