This function toggles the camera mode between a fixed view and the default player chase view. The camera's position and rotation in fixed mode can be set with the [setCameraPosition](/docs/setcameraposition.md "wikilink") and [setCameraLookAt](/setCameraLookAt.md "wikilink") functions respectively.

Syntax
------

``` lua
bool toggleCameraFixedMode ( bool fixed )
```

### Required Arguments

-   **fixed:** A boolean indicating the camera mode; *true* for fixed view, *false* for chase view.

### Returns

Returns a [bool](/docs/bool.md "wikilink") with a value of *true* if the function was successful, *false* otherwise.

Example
-------

**Example 1:** This example sets the player's camera above Blueberry Acres at a downward angle:

``` lua
toggleCameraFixedMode(true)
setCameraPosition(-16.268127441406, -46.674671173096, 29.565118789673)
setCameraLookAt(-68.21085357666, 34.687622070313, 11.11138343811)
```

**Example 2:** This example points the player's camera at the killer whenever the player dies:

``` lua
local thePlayer = getLocalPlayer() -- get the player running this client-side script
-- add an event handler to call the onDeath function whenever the player dies
function onDeath(theAttacker, weapon, bodypart)
    if (theAttacker and theAttacker ~= thePlayer) then -- make sure there is a killer
        -- store the position of the victim and killer
        local playerX, playerY, playerZ = getElementPosition(thePlayer)
        local attackerX, attackerY, attackerZ = getElementPosition(theAttacker)
        -- set the player's camera to fixed view
        toggleCameraFixedMode(true)
        -- set the camera's position at the player and in the killer's direction
        setCameraPosition(playerX, playerY, playerZ)
        setCameraLookAt(attackerX, attackerY, attackerZ)
        -- set the camera back to normal after 3 seconds
        setTimer(toggleCameraFixedMode, 3000, 1, false)
    end
end
addEventHandler("onClientPlayerWasted", thePlayer, onDeath)
```

See Also
--------
