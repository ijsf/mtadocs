This function is used to determine if an element is within a collision shape. Please note that for legacy reasons, a colshape created on the client does not collide with elements already existing at that location until they first move. Please also note that before 1.0.3, this did not function correctly when moving a colshape.

Please note that this function doesn't verify whether element is in the same dimension and interior, additional checks could be implemented manually if they are needed.

Syntax
------

``` lua
bool isElementWithinColShape ( element theElement, colshape theShape )
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") you're checking.
-   **theShape:** The [colshape](/docs/colshape.md "wikilink") you're checking

### Returns

Returns *true* if the element is within the colshape, *false* otherwise

Example
-------

This small script is an example of detecting if a player is within a certain defined colshape. This could serve as a base to perform many functions, rather than just an output.

``` lua
local circlearea = createColCircle ( 0, 0, 10 )

function ColShapeHit ( thePlayer, matchingDimension )
    local detection = isElementWithinColShape ( thePlayer, circlearea )
    --A variable called 'detection' stores the result of asking if the player
    --who entered a colshape is within the specific colshape called 'circlearea'.
    --The result is either true or false.
    detection = detection and getElementDimension( thePlayer ) == getElementDimension( circlearea )
    --Let's additionally check element dimensions.
    if detection then
        outputChatBox ( getPlayerName(thePlayer).." is in the 'circle area' col shape" )
    end
    --if detection was true then the player is in the col shape. Output a
    --message to confirm this
end
addEventHandler ( "onColShapeHit", root, ColShapeHit )
```

See Also
--------
