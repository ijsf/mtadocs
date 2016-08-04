This function allows detection of whether a radar area is flashing or not.

Syntax
------

``` lua
bool isRadarAreaFlashing ( radararea theRadararea )               
```

### Required Arguments

-   **theRadararea:** The radar area you wish to check the state of flashing

### Returns

Returns *true* if the radar area is flashing, *false* if it is not or if it doesn't exist.

Example
-------

This example checks whether the radar area in the variable *glenpark* is flashing, and announces it if it is.

``` lua
function checkArea(sourcePlayer)
    if ( isRadarAreaFlashing ( glenpark ) ) then          -- if the radar area in the variable glenpark is flashing
        outputChatBox ( "Glen Park is under attack!!!" )  -- announce it
    end
end
addCommandHandler("checkArea", checkArea)
```

See Also
--------
