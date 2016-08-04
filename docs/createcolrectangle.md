This function creates a collision rectangle. This is a shape that has a position and a width and a depth. See [Rectangle](http://en.wikipedia.org/wiki/Rectangle) for a definition of a rectangle. XY marks on the south west corner of the colshape.

Syntax
------

``` lua
colshape createColRectangle ( float fX, float fY, float fWidth, float fHeight)
```

### Required Arguments

-   **fX:** The X position of the collision rectangle's west side
-   **fY:** The Y position of the collision rectangle's south side
-   **fWidth:** The collision rectangle's width
-   **fHeight:** The collision rectangle's height

### Returns

Returns a [colshape](/docs/colshape.md "wikilink") element if successful, *false* if invalid arguments were passed to the function.

Example
-------

<section name="Server" class="server" show="true">
This example displays a chat message when a player enters the colshape and allows the colshape to be created using a console function *set\_zone*.

``` lua
theZone = false

function shapeHit ( thePlayer ) 
    outputChatBox ( getPlayerName ( thePlayer ) .. " is in the zone!" ) -- display a message in everyone's chat box
end

function setZone ( playerSource, commandName, fX, fY )
    if ( fY and fX ) then -- check we've got the 2 args we need
        local tempCol = createColRectangle ( fX, fY, 10.0, 10.0 ) -- create a col
        if ( tempCol == false ) then -- did the col get created successfully?
            outputConsole ( "Syntax is: set_zone <X> <Y>" ) -- inform the user what the valid syntax is
        else
            if ( theZone ~= false ) then -- did we already have a zone?
                destroyElement ( theZone ) -- if so, destroy it
            else
                   addEventHandler ( "onColShapeHit", theZone, shapeHit ) -- add a handler for the onColShapeHit event
            end
            theZone = tempCol -- and store the new zone we've made
            outputChatBox ( "Zone has moved!" ) -- and tell everyone
        end
    end
end
addCommandHandler ( "set_zone", setZone ) -- add a console function called set_zone that will trigger the function setZone
```

</section>
See Also
--------
