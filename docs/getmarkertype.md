This function returns a marker's type.

Syntax
------

``` lua
string getMarkerType ( marker theMarker )
```

### Required Arguments

-   **theMarker**: A [marker](/docs/marker.md "wikilink") element referencing the specified marker.

### Returns

-   Returns one of the following strings:

If an invalid marker is specified, *false* is returned.

Example
-------

<section name="Client and server" class="both" show="true">
This function creates a default marker at a given position and outputs its type.

``` lua
function createMarkerAndOutputType ( x, y, z )
    -- we create the marker
    local theMarker = createMarker ( x, y, z )
    -- if the marker was created,
    if ( theMarker ) then
        -- then get its type,
        local markerType = getMarkerType ( theMarker )
        -- and output it.
        outputChatBox ( "It's a " .. markerType .. " marker!" )
    end
    -- return the created marker element (or false) where this function was called
    return theMarker
end
```

</section>
See Also
--------
