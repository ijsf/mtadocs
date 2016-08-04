This function creates a collision tube. This is a shape that has a position and a 2D (X/Y) radius and a height. See [Cylinder](http://en.wikipedia.org/wiki/Cylinder_(geometry)) for a definition of a tube. A tube is similar to a colcircle, except that it has a limited height, this means you can limit the distance above the position defined by (fX, fY, fZ) that the collision is detected.

Syntax
------

``` lua
colshape createColTube ( float fX, float fY, float fZ, float fRadius, float fHeight)
```

### Required Arguments

-   **fX:** The position of the base of the tube's center on the X axis
-   **fY:** The position of the base of the tube's center on the Y axis
-   **fZ:** The position of the base of the tube's center on the Z axis
-   **fRadius:** The collision tube's radius
-   **fHeight:** The collision tube's height

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

function setZone ( playerSource, commandName, fX, fY, fZ )
    if ( fZ and fY and fX ) then -- check we've got all 3 args we need
        local tempCol = createColTube ( fX, fY, fZ, 10.0, 10.0 ) -- create a col
        if ( tempCol == false ) then -- did the col get created successfully?
            outputConsole ( "Syntax is: set_zone <X> <Y> <Z>" ) -- inform the user what the valid syntax is
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
