<lowercasetitle></lowercasetitle>

This function checks one argument up to many, this is really handy for checking illegal weapons.

Syntax
------

``` lua
boolean multi_check( *source, mixed ... )
```

### Required Arguments

-   **source**: The base element to check up against
-   **...**: Many arguments witch will be checked up against the **source**

Code
----

<section name="Function source" class="both" show="true">
``` lua
function multi_check( source, ... )
    local arguments = { ... };

    for _, argument in ipairs( arguments ) do
        if argument == source then
            return true;
        end
    end
    return false;
end
```

</section>
Example
-------

<section name="Example" class="both" show="true">
``` lua
addEventHandler( "onPlayerWeaponSwitch", getRootElement( ),
    function( previousWeapon, currentWeapon )
                local check = multi_check( currentWeapon, 1, 2, 3 );
        if check then
            outputChatBox( "You are not allowed to use that weapon", source );
        end
            toggleControl( source, "fire", not check );
    end
);
```

</section>
Function created by **Alexander de Jong AKA mrdejong**.

See Also
--------
