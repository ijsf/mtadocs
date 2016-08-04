This function can be used to create custom radar areas on the radar.

Syntax
------

``` lua
radararea createRadarArea ( float leftX, float bottomY, float sizeX, float sizeY, [ int r = 255, int g = 0, int b = 0, int a = 255, element visibleTo = getRootElement() ] )             
```

### Required Arguments

-   **leftX:** A float representing the left 'x' position of the radar area.
-   **bottomY:** A float representing the bottom 'y' position of the radar area.
-   **sizeX:** A float representing the width of the radar area.
-   **sizeY:** A float representing the height of the radar area.

<!-- -->

-   **r:** An integer representing the amount of red in the color. Maximum value is 255
-   **g:** An integer representing the amount of green in the color. Maximum value is 255
-   **b:** An integer representing the amount of blue in the color. Maximum value is 255
-   **a:** An integer representing the amount of alpha in the color. This allows setting the transparency of the radar area. 255 is opaque and 0 is transparent.

### Optional Arguments

-   **visibleTo:** An [element](/element.md "wikilink") that you wish to restrict the [visibility](/visibility.md "wikilink") of the radar area to. (Server function only)

Example
-------

<section name="Server" class="server" show="true">
This example creates a radar area for the King of the hill script, and a colsquare. When the player enters the radar area it flashes, and stops flashing when a player leaves it.

``` lua
-- create our hill area for our gamemode
local hillArea = createColRectangle ( -2171.0678710938, 678.17950439453, 15, 15 )
local hillRadar = createRadarArea ( -2183.5678710938, 705.67950439453, 40, -40, 0, 255, 0, 175 )

-- add hill_Enter as a handler for when a player enters the hill area
function hill_Enter ( thePlayer, matchingDimension )
        -- announce to everyone that the player entered the hill
        if (getElementType(thePlayer) == "player") then
                outputChatBox( getPlayerName(thePlayer) .. " entered the zone!", getRootElement(), 255, 255, 109 )
                setRadarAreaFlashing ( hillRadar, true )
        end
end
addEventHandler ( "onColShapeHit", hillArea, hill_Enter )

-- add hill_Enter as a handler for when a player leaves the hill area
function hill_Exit ( thePlayer, matchingDimension )
        -- check if the player is not dead
        if (getElementType(thePlayer) == "player") then
                if isPedDead ( thePlayer ) ~= true then
                        -- if he was alive, announce to everyone that the player has left the hill
                        outputChatBox ( getPlayerName(thePlayer) .. " left the zone!", getRootElement(), 255, 255, 109 )
                        setRadarAreaFlashing ( hillRadar, false )
                end
        end
end
addEventHandler ( "onColShapeLeave", hillArea, hill_Exit )
```

</section>
See Also
--------
