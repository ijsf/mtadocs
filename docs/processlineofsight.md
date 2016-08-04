This function casts a ray between two points in the world, and tells you information about the point that was hit, if any. The two positions **must** be within the local player's draw distance as the collision data is not loaded outside this area, and the call will just fail as if the ray didn't hit.

This function is relatively expensive to call, so over use of this in scripts may have a detrimental effect on performance.

This function is useful for checking for collisions and for editor-style scripts. If you wish to find what element is positioned at a particular point on the screen, use this function combined with [getWorldFromScreenPosition](/docs/getworldfromscreenposition.md "wikilink"). If you wish to just know if something is hit, and don't care about what or where was hit, use [isLineOfSightClear](/isLineOfSightClear.md "wikilink").

Syntax
------

Return values labelled for ease of reference.

``` lua
bool               -- hit
float float float  -- hitX, hitY, hitZ
element            -- hitElement
float float float  -- normalX, normalY, normalZ
int                -- material
float              -- lighting
int                -- piece
int                -- worldModelID
float float float  -- worldModelPositionX,Y,Z
float float float  -- worldModelRotationX,Y,Z
int                -- worldLODModelID
                  processLineOfSight ( float startX, float startY, float startZ, 
                                       float endX, float endY, float endZ, 
                                       [ bool checkBuildings = true, 
                                       bool checkVehicles = true, 
                                       bool checkPlayers = true, 
                                       bool checkObjects = true, 
                                       bool checkDummies = true, 
                                       bool seeThroughStuff = false, 
                                       bool ignoreSomeObjectsForCamera = false, 
                                       bool shootThroughStuff = false, 
                                       element ignoredElement = nil,
                                       bool includeWorldModelInformation = false,
                                       bool bIncludeCarTyres ] )
```

### Required Arguments

-   **startX:** The start *x* position
-   **startY:** The start *y* position
-   **startZ:** The start *z* position
-   **endX:** The end *x* position
-   **endY:** The end *y* position
-   **endZ:** The end *z* position

### Optional Arguments

-   **checkBuildings:** Allow the line of sight to be blocked by GTA's internally placed buildings, i.e. the world map.
-   **checkVehicles:** Allow the line of sight to be blocked by [vehicles](/docs/vehicle.md "wikilink").
-   **checkPlayers:** Allow the line of sight to be blocked by [players](/docs/player.md "wikilink").
-   **checkObjects:** Allow the line of sight to be blocked by [objects](/docs/object.md "wikilink").
-   **checkDummies:** Allow the line of sight to be blocked by GTA's internal dummies. These are not used in the current MTA version so this argument can be set to *false*.
-   **seeThroughStuff:** Allow the line of sight to be blocked by translucent game objects, e.g. glass.
-   **ignoreSomeObjectsForCamera:** Allow the line of sight to pass through objects that have (K) property enabled in “object.dat” data file. (i.e. Most dynamic objects like boxes or barrels)
-   **shootThroughStuff:** Allow the line of sight to be blocked by things that can be shot through
-   **ignoredElement:** Allow the line of sight to pass through a certain specified element. This is usually set to the object you are tracing from so it does not interfere with the results.
-   **includeWorldModelInformation :** Include the results of hitting a world model.
-   **bIncludeCarTyres :** Includes car tyre hits.

### Returns

-   **hit:** *true* if there is a collision, *false* otherwise

The other values are only filled if there is a collision, they contain *nil* otherwise

-   **hitX, hitY, hitZ:** collision position
-   **hitElement:** the MTA element hit if any, *nil* otherwise
-   **normalX, normalY, normalZ:** the normal of the surface hit
-   **material:** an integer representing the [GTASA material ID](/docs/material_ids.md "wikilink") of the surface hit when applicable (world, objects)
-   **lighting:** a float between 0 (fully dark) and 1 (bright) representing the amount of light that the hit building surface will transfer to peds or vehicles that are in contact with it. The value can be affected by the game time of day, usually with a lower (darker) value being returned during the night.
-   **piece:** an integer representing the part of the element hit if hitElement is a vehicle or a ped/player, *0* otherwise.
    -   For a ped/player, piece represents the body part hit:

-   -   For vehicles, piece represents the vehicle part hit:

-   **worldModelID:** If includeWorldModelInformation was set to *true* and a world model was hit, this will contain the model ID.
-   **worldModelPositionX,Y,Z:** If worldModelID is set, this will contain the world model position.
-   **worldModelRotationX,Y,Z:** If worldModelID is set, this will contain the world model rotation.
-   **worldLODModelID:** If worldModelID is set, this will contain the LOD model ID if applicable.

Examples
--------

This example shows how you can tell what position and element the camera is looking at, up to 50 units away.

``` lua
local w, h = guiGetScreenSize ()
local tx, ty, tz = getWorldFromScreenPosition ( w/2, h/2, 50 )
local px, py, pz = getCameraMatrix()
hit, x, y, z, elementHit = processLineOfSight ( px, py, pz, tx, ty, tz )
if hit then
    outputChatBox ( "Looking at " .. x .. ", " .. y .. ", " ..  z )
    if elementHit then
        outputChatBox ( "Hit element " .. getElementType(elementHit) )
    end
end
```

This example shows how you can get the surface type a vehicle is on. This is useful if you want to do a script to dirt cars over time. Please note that this function doesn't count if the vehicle is streamed in or not, so expect this function to fail or return incorrect values on unloaded vehicles.

``` lua
function getSurfaceVehicleIsOn(vehicle)
    if isElement(vehicle) and (isVehicleOnGround(vehicle) or isElementInWater(vehicle)) then -- Is an element and is touching any surface?
        local cx, cy, cz = getElementPosition(vehicle) -- Get the position of the vehicle
        local gz = getGroundPosition(cx, cy, cz) - 0.001 -- Get the Z position of the ground the vehicle is on (-0.001 because of processLineOfSight)
        local hit, _, _, _, _, _, _, _, surface = processLineOfSight(cx, cy, cz, cx, cy, gz) -- This will get the material of the thing the car is standing on
        if hit then
            return surface -- If everything is correct, stop executing this function and return the surface type
        end
    end
    return false -- If something isn't correct, return false
end
```

Changelog
---------

See Also
--------
