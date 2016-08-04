This function creates a collision cuboid. This is a shape that has a position, width, depth and height. See [Wikipedia](http://en.wikipedia.org/wiki/Cuboid) for a definition of a cuboid. The XYZ of the col starts at the southwest bottom corner of the shape.

Syntax
------

``` lua
colshape createColCuboid ( float fX, float fY, float fZ, float fWidth, float fDepth, float fHeight )
```

### Required Arguments

-   **fX:** The X position of the collision cuboid's western side
-   **fY:** The Y position of the collision cuboid's southern side
-   **fZ:** The Z position of the collision cuboid's lowest side
-   **fWidth:** The collision cuboid's width
-   **fDepth:** The collision cuboid's depth
-   **fHeight:** The collision cuboid's height

### Returns

Returns a [colshape](/docs/colshape.md "wikilink") element if successful, *false* if invalid arguments were passed to the function.

Example
-------

<section name="Server" class="server" show="true">
This example displays a chat message when a player enters the colshape and allows the colshape to be created using a console function *set\_zone*.

``` lua
theZone = false

function shapeHit ( thePlayer ) 
    outputChatBox ( getPlayerName ( thePlayer ) .. " is in the zone!" )  -- display a message in everyone's chat box
end

function setZone ( playerSource, commandName, fX, fY, fZ )
    if ( fZ and fY and fX ) then                                         -- check we've got all 3 args we need
        local tempCol = createColCuboid ( fX, fY, fZ, 10.0, 10.0, 10.0 )   -- create a col
        if ( tempCol == false ) then                                     -- did the col get created successfully?
            outputConsole ( "Syntax is: set_zone <X> <Y> <Z>" )          -- inform the user what the valid syntax is
        else
            if ( theZone ~= false ) then                                 -- did we already have a zone?
                destroyElement ( theZone )                               -- if so, destroy it
            else
                addEventHandler ( "onColShapeHit", theZone, shapeHit )   -- add a handler for the onColShapeHit event
            end
            theZone = tempCol                                            -- store the new zone we've made
            outputChatBox ( "Zone has moved!" )                          -- and tell everyone
        end
    end
end
addCommandHandler ( "set_zone", setZone ) -- add a console function called set_zone that will trigger the function setZone
```

</section>
See Also
--------
