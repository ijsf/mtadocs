This function returns the position of the specified marker's target, the position it points to. This only works for checkpoint markers and ring markers. For checkpoints it returns the position the arrow is pointing to, for ring markers it returns the position the ring is facing. You can set this target with [setMarkerTarget](/docs/setmarkertarget.md "wikilink").

Syntax
------

``` lua
float float float getMarkerTarget ( marker theMarker )   
```

### Required Arguments

-   **theMarker:** The marker you wish to retrieve the target position of.

### Returns

Returns three *float*s if a target is set, or *false* in the first variable and *nil* in the two others if the marker is invalid or no target is set.

Example
-------

This example outputs the markers target (if available) when a player hits a marker.

<section show="true" name="Server" class="server">
``` lua
function nextCheck(thePlayer)
    local x,y,z = getMarkerTarget(source)    -- get the marker target
    if x ~= false then                       -- if a target is set for the marker, then...
        outputChatBox("Next checkpoint at: " .. x .. " " .. y .. " " .. z, thePlayer) -- output a message with the coordinates
    end
end
addEventHandler("onMarkerHit", getRootElement(), nextCheck) -- add an event handler for the 'onMarkerHit' event
```

</section>
See Also
--------
