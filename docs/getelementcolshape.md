This function is used to get element's colshape.

Syntax
------

``` lua
colshape getElementColShape ( element theElement )          
```

### Required Arguments

-   **theElement:** The element you want to get the colshape of

### Returns

Returns *colshape* of the element, *false* if not or an invalid argument was passed to the function.

Example
-------

<section class="server" name="Server" show="true">
This example creates a marker inside Toreno's house and adds a command to check whether you are standing on it.

``` lua
theMarker = createMarker( -687.9, 937.8, 13.6, "cylinder", 2.0, 255, 0, 0, 80 ) -- create a red cylinder marker inside Toreno's house

function checkOnMarker ( thePlayer )
    local isIn = isPlayerInMarker( thePlayer, theMarker ) -- use the function to check if player is in the marker
    if isIn then
        outputChatBox( "You are on the marker.", thePlayer )
    else
        outputChatBox( "You are not on the marker.", thePlayer )
    end
end
addCommandHandler ( "amionmarker", checkOnMarker )

-- define the isPlayerInMarker function
function isPlayerInMarker( thePlayer, theMarker )
    local theShape = getElementColShape( theMarker ) -- get markers colshape
    if isElementWithinColShape( thePlayer, theShape ) then -- check if the player is in it
        return true
    else -- he isn't on the marker
        return false
    end
end
```

</section>
See Also
--------
