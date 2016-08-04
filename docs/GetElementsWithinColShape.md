This function is used to retrieve a list of all elements in a colshape, of the specified type. Please note that for legacy reasons, a colshape created on the client does not collide with elements already existing at that location until they first move. Please also note that before 1.0.3, this did not function correctly when moving a colshape

Please note that this function doesn't verify whether elements are in the same dimension and interior, additional checks could be implemented manually if they are needed.

Syntax
------

``` lua
table getElementsWithinColShape ( colshape shape, [ string elemType = nil ] ) 
```

### Required Arguments

-   **shape:** The colshape you want to get the elements from.

### Optional Arguments

-   **elemType:** The type of element you want a list of. This can be any element type, the common ones being:
    -   **“player”:** A player connected to the server
    -   **“ped”:** A ped
    -   **“vehicle”:** A vehicle
    -   **“object”:** An object
    -   **“pickup”:** A pickup
    -   **“marker”:** A marker

### Returns

Returns a *table* containing all the elements inside the colshape, of the specified type. Returns an empty *table* if there are no elements inside. Returns *false* if the colshape is invalid.

Example
-------

This example retrieves a table of the players in the colshape and prints their name to the chat.

``` lua
local newcolshape = createColSphere ( 1, 2, 3, 4 )
local players = getElementsWithinColShape ( newcolshape, "player" )  -- get all the players inside the sphere
for theKey,thePlayer in ipairs(players) do                           -- use a generic for loop to step through each player
    outputChatBox ( getPlayerName ( thePlayer ) .. " is in our new sphere" )  -- print their name to the chat
end
```

See Also
--------
