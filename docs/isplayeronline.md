This function checks if a player is online.

Syntax
------

``` lua
bool isPlayerOnline( string playerToCheck )
```

### Required Arguments

-   **playerToCheck**: The players name to check.

### Returns

Returns true if player is online else false.

Code
----

``` lua
function isPlayerOnline ( name )  
    if isElement(getPlayerFromName(name)) then
        return true
    end
    return false
end
```

See Also
--------
