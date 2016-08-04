This function sets the ID of an element to a string. This can be anything from an identifying number, to a name. You can only change the ID of an element clientside if that element has been created clientside as well.

Syntax
------

``` lua
bool setElementID ( element theElement, string name ) 
```

### Required Arguments

-   **theElement:** The [element](/element.md "wikilink") you want to set the ID of.
-   **name:** The new ID for theElement.

### Returns

This returns *true* if successful. It will return *false* if **theElement** is invalid, or does not exist, or if **name** is invalid, or is not a string.

Example
-------

``` lua
local players = getElementsByType( "player" )
 
for i=1,#players do
   setElementID( players[i], "player" .. i )    -- Change element IDs to 'player1', 'players2', 'players3'...
   outputDebugString( "Player[" .. i .. "] = " .. getElementID( players[i] ) ) -- Output all the new element IDs
end

-- Could also be --

for i=1,#players do
   setElementID( players[i], getPlayerName( players[i] ) )  -- Change the element ID to the players name.
   outputDebugString( "Player[" .. i .. "] = " .. getElementID( players[i] ) )
end
```

See Also
--------
