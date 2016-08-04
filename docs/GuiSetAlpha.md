This changes the alpha level (the visibleness/transparency) of a GUI element

Syntax
------

``` lua
bool guiSetAlpha ( element guielement, float alpha )
```

### Required Arguments

-   **guiElement:** the GUI element whose visibility is to be changed
-   **alpha:** The visibility/transparency of the GUI element. Ranges from 0 (fully transparent) to 1 (fully opaque). Default value is 0.80.

### Returns

Returns *true* if the gui element's alpha was successfully changed, *false* otherwise.

Example
-------

This creates a GUI window and allows a player to change it's alpha (the visibleness/transparency) value with a command.

``` lua
--Create a gridlist
myWindow = guiCreateWindow ( 0.30, 0.10, 0.5, 0.60, "GUI window title", true )

--Add a command handler to change the alpha of the GUI window.
--Usage example: '/alpha 0.8', where 0.8 is stored as alphaAmount
function changeAlpha ( commandName, alphaAmount )
        alphaAmount = tonumber(alphaAmount)
        guiSetAlpha ( myWindow, alphaAmount )
end
addCommandHandler ( "alpha", changeAlpha )
```

See Also
--------
