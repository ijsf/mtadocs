Syntax
------

``` lua
 )
```

### Required Arguments

-   **name:** A string contains [effect name](/docs/element/effect#effects_list.md "wikilink").
-   **x:** A floating point number representing the X coordinate on the map.
-   **y:** A floating point number representing the Y coordinate on the map.
-   **z:** A floating point number representing the Z coordinate on the map.

### Optional Arguments

-   **rX:** A floating point number representing the rotation about the X axis in degrees.
-   **rY:** A floating point number representing the rotation about the Y axis in degrees.
-   **rZ:** A floating point number representing the rotation about the Z axis in degrees.

### Returns

Returns the [effect](/docs/element/effect.md "wikilink") element if creation was successful, *false* otherwise.

Example
-------

``` lua
addCommandHandler("effect", 
    function(cmd, name)
        local x, y, z = getElementPosition(localPlayer)
        if createEffect(name, x, y, z) then
            outputChatBox("Effect created!")
        else
            outputChatBox("Bad effect name.")
        end
    end
)
```

Changelog
---------

See Also
--------

[ru:createEffect](/docs/ru:createeffect.md "wikilink")
