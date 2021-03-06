This function creates a collision polygon. See [Wikipedia](http://en.wikipedia.org/wiki/Polygon) for a definition of a polygon. The first set of X Y of this shape is not part of the colshape bounds, so can set anywhere in the game world, however for performance, place it as close to the centre of the polygon as you can. It should be noted this shape is **2D**. There should be at least 3 bound points set.

Syntax
------

``` lua
colshape createColPolygon ( float fX, float fY, float fX1, float fY1, float fX2, float fY2, float fX3, float fY3, ... )
```

### Required Arguments

-   **fX:** The X position of the collision polygon's position - the position that will be returned from [getElementPosition](/docs/getelementposition.md "wikilink").
-   **fY:** The Y position of the collision polygon's position - the position that will be returned from [getElementPosition](/docs/getelementposition.md "wikilink").
-   **fX1:** The 1st X position of the collision polygon's bound point
-   **fY1:** The 1st Y position of the collision polygon's bound point
-   **fX2:** The 2nd X position of the collision polygon's bound point
-   **fY2:** The 2nd Y position of the collision polygon's bound point
-   **fX3:** The 3rd X position of the collision polygon's bound point
-   **fY3:** The 3rd Y position of the collision polygon's bound point
-   **...** From the 3rd position you can have as many points as you require to create the colshape.

### Returns

Returns a [colshape](/docs/colshape.md "wikilink") element if successful, *false* if invalid arguments were passed to the function.

Example
-------

<section name="Server" class="server" show="true">
This example displays a chat message when a player enters the colshape and allows the colshape to be created using a console function *set\_zone*.

``` lua
theZone = false
 
function shapeHit ( thePlayer ) 
    outputChatBox ( getPlayerName ( thePlayer ) .. " is in the zone!" )                -- display a message in everyone's chat box
end
 
function setZone ( playerSource, commandName, fX, fY, fX1, fY1, fX2, fY2, fX3, fY3 )   --Remember that after the 3rd position you 
                                                                                       --can have as many points as you require to 
                                                                                       --create the colshape.

    if ( fY and fX and fX1 and fY1 and fX2 and fX3 and fY3 ) then                      -- check we've got the 8 args we need
        local tempCol = createColPolygon ( fX, fY, fX1, fY1, fX2, fY2, fX3, fY3 )      -- create a col
        if ( tempCol == false ) then                                                   -- did the col get created successfully?
            outputConsole ("Syntax is: set_zone <X> <Y> <X1> <Y1> <X2> <Y2> <X3> <Y3>")-- inform the user what the valid syntax is
        else
            if ( theZone ~= false ) then                                               -- did we already have a zone?
                destroyElement ( theZone )                                             -- if so, destroy it
            else
                   addEventHandler ( "onColShapeHit", theZone, shapeHit )              -- add a handler for the onColShapeHit event
            end
            theZone = tempCol                                                          -- and store the new zone we've made
            outputChatBox ( "Zone has moved!" )                                        -- and tell everyone
        end
    end
end
addCommandHandler ( "set_zone", setZone )         -- add a console function called set_zone that will trigger the function setZone
```

</section>
See Also
--------
