This event is triggered when a physical [element](/element.md "wikilink") hits a [colshape](/colshape.md "wikilink").

**NOTE**: The hit won't be detected if the [element](/element.md "wikilink") that entered the colshape is a colshape.

Parameters
----------

``` lua
element hitElement, bool matchingDimension
```

-   **hitElement**: the [element](/element.md "wikilink") that entered the colshape.
-   **matchingDimension**: a boolean referring to whether the hit collision shape was in the same dimension as the element.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [colshape](/colshape.md "wikilink") that got hit by a player or vehicle.

Example
-------

This example creates a hill area for a *King of the hill* gamemode. When a player enters or leaves the area, it's announced in the chatbox.

``` lua
-- create our hill area for our gamemode
local hillArea = createColRectangle ( -2171.0678710938, 678.17950439453, 15, 15 )

-- add hill_Enter as a handler for when a player enters the hill area
function hill_Enter ( thePlayer, matchingDimension )
        if getElementType ( thePlayer ) == "player" then --if the element that entered was player
                --let's get the name of the player
                local nameOfThePlayer = getPlayerName ( thePlayer )
            --announce to everyone that the player entered the hill
            outputChatBox ( nameOfThePlayer.." entered the zone!", getRootElement(), 255, 255, 109 )
        end
end
addEventHandler ( "onColShapeHit", hillArea, hill_Enter )

-- add hill_Enter as a handler for when a player leaves the hill area
function hill_Exit ( thePlayer, matchingDimension )
        if getElementType ( thePlayer ) == "player" then --if the element that left was player
            --check if the player is not dead
            if isPlayerDead ( thePlayer ) ~= true then
                        --let's get the name of the player
                        local nameOfThePlayer = getPlayerName ( thePlayer )
                --if he was alive, announce to everyone that the player has left the hill
                outputChatBox ( nameOfThePlayer.." left the zone!", getRootElement(), 255, 255, 109 )
            end
        end
end
addEventHandler ( "onColShapeLeave", hillArea, hill_Exit )
```
