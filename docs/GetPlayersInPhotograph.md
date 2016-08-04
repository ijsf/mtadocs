This function can be used with any weapon, but is more accurate when executed when the player shoots the weapon and the weapon is a camera.
\* **NOTE:** This is made to be used clientside!.

Syntax
------

``` lua
table getPlayersInPhotograph( )
```

### Required Arguments

-   none

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function getPlayersInPhotograph()
    local players = {}
    local nx, ny, nz = getPedWeaponMuzzlePosition(localPlayer)
    
    for _, v in ipairs(getElementsByType"player") do
               
                -- Determine whether the player is even on the screen, or the client is the player.
        if (v ~= localPlayer) and (isElementOnScreen(v)) then
            local veh = getPedOccupiedVehicle(v)
            local px, py, pz = getElementPosition(v)
            local _, _, _, _, hit = processLineOfSight(nx, ny, nz, px, py, pz) -- Check if there is a collision between the "camera viewpoint" and the player
            local continue = false
            
            if (hit == v) or (hit == veh) or (not veh) then -- If it collides with the player itself, the client or the players vehicle, continue to add player to the list.
                continue = true
            else -- This checks if the player's head is visible, but not the entire body
                local bx, by, bz = getPedBonePosition(v, 8) -- Get the head position of the player
                local _, _, _, _, hit = processLineOfSight(nx, ny, nz, px, py, pz) -- Check if there is a collision between the "camera viewpoint" and player head.
                
                if hit == v then
                    continue = true
                end
            end
            
            if continue then
                table.insert(players, v)
            end
        end
    end
    
    return players
end
```

</section>
Example
-------

This example center the window.

``` lua
-- todo
```

Author: qaisjp

See Also
--------
