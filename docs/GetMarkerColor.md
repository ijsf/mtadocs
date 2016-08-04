This function returns the color and transparency for a marker element. Not all marker types support transparency.

Syntax
------

``` lua
int, int, int, int getMarkerColor ( marker theMarker )
```

### Required Arguments

-   **theMarker**: The [marker](/docs/marker.md "wikilink") that you wish to retrieve the color of.

### Returns

Returns four [ints](/docs/int.md "wikilink") corresponding to the amount of *red*, *green*, *blue* and *alpha* (respectively) of the marker, *false* if invalid arguments were passed.

Example
-------

<section name="Serverside example" class="server" show="true">
This example script fully heals players who hit a white marker, and kills players who hit a red one.

``` lua
-- we define the function that will determine if the player is to be healed or killed
function healOrKill ( hitMarker, matchingDimension )
    -- if the marker was in a different dimension, stop here to ignore the event
    if not matchingDimension then
        return
    end
    -- get the marker's color
    local R, G, B, A = getMarkerColor( hitMarker )
    -- if its RGB color is 255,255,255 (white),
    if R == 255 and G == 255 and B == 255 then
        -- heal the player
        setElementHealth( source, 100 )
    -- if it isn't white, but 255,0,0 (red),
    elseif R == 255 and G == 0 and B == 0 then
        -- kill the player
        killPed( source )
    end
end
-- add our function as a handler to "onPlayerMarkerHit"
addEventHandler( "onPlayerMarkerHit", getRootElement(), healOrKill )
```

</section>
See Also
--------
