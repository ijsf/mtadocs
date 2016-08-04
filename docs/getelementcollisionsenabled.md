This function indicates if a specific element is set to have collisions disabled. An element without collisions does not interact with the physical environment and remains static.

Syntax
------

``` lua
bool getElementCollisionsEnabled ( element theElement ) 
```

### Required Arguments

-   **theElement:** The element for which you want to check whether collisions are enabled

### Returns

Returns *true* if the collisions are enabled, *false* otherwise.

Example
-------

This example check if there are any players with collisions disabled.

``` lua
for _,player in ipairs( getElementsByType( "player" ) ) do
   if not getElementCollisionsEnabled( player ) then -- If we get a false return from the function, we know that the collisions are disabled.
      outputConsole( "Player " .. getPlayerName( player ) .. " has collisions disabled." ) 
   end
end
```

See Also
--------
