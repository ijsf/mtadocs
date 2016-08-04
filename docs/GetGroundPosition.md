This function gets the Z level of the highest ground below a point.

It is required that the point is near enough to the local player so that it's within the area where collision data is loaded. If this is not the case, an incorrect position will be returned.

Syntax
------

``` lua
float getGroundPosition ( float x, float y, float z )
```

### Required Arguments

-   **x:** A floating point number representing the X world coordinate of the point.
-   **y:** A floating point number representing the Y world coordinate of the point.
-   **z:** A floating point number representing the Z world coordinate of the point.

### Returns

Returns a float with the highest ground-level Z coord if parameters are valid, *0* if the point you tried to test is outside the loaded world map, *false* otherwise.

Example
-------

This clientside function determines if a player is under a ceiling or not.

``` lua
function isPlayerUnderCover ( thePlayer )
    --we get the player's position
    local px, py, pz = getElementPosition ( thePlayer )
    --we'll check for ground level at the player's position, and also 500 units over him.
    --if these ground levels match, it must mean there were no obstacles (such as a ceiling) over the player,
    if getGroundPosition ( px, py, pz ) == getGroundPosition ( px, py, pz + 500 ) then
        -- so the player is not under cover
        return false
    --otherwise, there was an object over him,
    else
        -- so the player is under cover
        return true
    end
end
```

See Also
--------

[ru:getGroundPosition](/ru:getGroundPosition.md "wikilink")
