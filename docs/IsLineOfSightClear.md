This function checks if there are obstacles between two points of the game world, optionally ignoring certain kinds of elements. Use [processLineOfSight](/processLineOfSight.md "wikilink") if you want more information about what the ray hits.

Syntax
------

``` lua
bool isLineOfSightClear ( float startX, float startY, float startZ, float endX, float endY, float endZ, [ bool checkBuildings = true, bool checkVehicles = true, bool checkPeds = true, bool checkObjects = true, bool checkDummies = true, bool seeThroughStuff = false, bool ignoreSomeObjectsForCamera = false, element ignoredElement = nil ] )
```

### Required Arguments

-   **startX:** The first point's world X coordinate.
-   **startY:** The first point's world Y coordinate.
-   **startZ:** The first point's world Z coordinate.
-   **endX:** The second point's world X coordinate.
-   **endY:** The second point's world Y coordinate.
-   **endZ:** The second point's world Z coordinate.

### Optional Arguments

-   **checkBuildings:** Allow the line of sight to be blocked by GTA's internally placed buildings, i.e. the world map.
-   **checkVehicles:** Allow the line of sight to be blocked by [vehicles](/Vehicle.md "wikilink").
-   **checkPeds:** Allow the line of sight to be blocked by peds, i.e. [players](/Player.md "wikilink").
-   **checkObjects:** Allow the line of sight to be blocked by [objects](/Object.md "wikilink").
-   **checkDummies:** Allow the line of sight to be blocked by GTA's internal dummies. These are not used in the current MTA version so this argument can be set to *false*.
-   **seeThroughStuff:** Allow the line of sight to be blocked by translucent game objects, e.g. glass.
-   **ignoreSomeObjectsForCamera:** Allow the line of sight to be blocked by certain objects.
-   **ignoredElement:** Allow the line of sight to pass through a certain specified element.

### Returns

Returns *true* if the line between the specified points is clear, *false* if there's an obstacle or if invalid parameters are passed.

Example
-------

<section name="Client" class="client" show="false">
isLineOfSightClear is the economical way to cast a ray in the world. This example demonstrates how you can easily implement basic NPC behaviour such as jumping obstacles. A 3D line is drawn connecting the two points in the ray.

``` lua
local t_Data = {}

local function updateNPC ()
    if (not isElement(t_Data.ped) or (getElementHealth(t_Data.ped) == 0)) then
        return toggleNPCFollower ()
    end
    
    local t_PlayerPos = {getElementPosition(localPlayer)}
    local t_PedPos = {getElementPosition(t_Data.ped)}
    
    local intDistance = getDistanceBetweenPoints3D (t_PedPos[1], t_PedPos[2], t_PedPos[3], unpack(t_PlayerPos))
    if (intDistance < 4) then
        setPedControlState (t_Data.ped, 'forwards', false)
        return true
    end
    
    -- Calculate the rotation between ped and player position
    local intPedRot = -math.deg (math.atan2(t_PlayerPos[1] - t_PedPos[1], t_PlayerPos[2] - t_PedPos[2]))
    if intPedRot < 0 then intPedRot = intPedRot + 360 end;
    
    setElementRotation (t_Data.ped, 0, 0, intPedRot, 'default', true)
    -- At this point we know that the ped needs to move it
    setPedControlState (t_Data.ped, 'forwards', true)
    
    local bPathClear = true
    local t_Matrix = getElementMatrix (t_Data.ped)
    
    -- Calculate a position 1m ahead of ped
    local int_RayX = t_Matrix[2][1] + t_Matrix[4][1]
    local int_RayY = t_Matrix[2][2] + t_Matrix[4][2]
    local int_RayZ = t_Matrix[2][3] + t_Matrix[4][3]
    
    -- We cast 10 rays 1m ahead of the ped
    for i = 1, 10 do
        local intSourceX, intSourceY, intSourceZ = t_PedPos[1], t_PedPos[2], t_PedPos[3]
        
        -- The target position height is identical to the center of the ped (1m above ground) 
        -- We lower this value by 0.5m to detect short obstacles
        local intTargetX, intTargetY, intTargetZ = int_RayX, int_RayY, int_RayZ - 0.5 + i*0.2
        
        bPathClear = isLineOfSightClear (intSourceX, intSourceY, intSourceZ, intTargetX, intTargetY, intTargetZ, true, true, false, true)
        dxDrawLine3D (intSourceX, intSourceY, intSourceZ, intTargetX, intTargetY, intTargetZ, bPathClear and tocolor(255,255,255,255) or tocolor(255,0,0,255))
        
        if (not bPathClear) then
            break
        end
    end
    
    if (not bPathClear) then
        setPedControlState (t_Data.ped, 'jump', true)
    else
        setPedControlState (t_Data.ped, 'jump', false)
    end
    
    if (intDistance > 15) then
        setPedControlState (t_Data.ped, 'sprint', true)
    else
        setPedControlState (t_Data.ped, 'sprint', false)
    end
end

function toggleNPCFollower ()
    if (t_Data.ped) then
        if (t_Data.updateNPCTimer) then
            if (isTimer(t_Data.updateNPCTimer)) then
                killTimer (t_Data.updateNPCTimer)
            end
        end
        if (isElement(t_Data.ped)) then
            destroyElement (t_Data.ped)
        end
        t_Data.ped = nil
        return true
    end

    local intX, intY, intZ = getElementPosition (localPlayer)
    local _, _, intRZ = getElementRotation (localPlayer)
    local t_Matrix = getElementMatrix (localPlayer)
    
    -- Calculate a position 4m behind local player
    local intPedX = -4 * t_Matrix[2][1] + t_Matrix[4][1]
    local intPedY = -4 * t_Matrix[2][2] + t_Matrix[4][2]
    local intPedZ = -4 * t_Matrix[2][3] + t_Matrix[4][3]
    
    t_Data.ped = createPed (0, intPedX, intPedY, intPedZ, intRZ)
    t_Data.updateNPCTimer = setTimer (updateNPC, 50, 0)
end
addCommandHandler ('npc', toggleNPCFollower)
```

</section>
See Also
--------
