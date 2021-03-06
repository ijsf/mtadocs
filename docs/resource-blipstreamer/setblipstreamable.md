This function enables a blip to automatically stream according to the radius

Syntax
------

``` lua
bool setBlipStreamable ( element blip, bool streamingEnabled [, float radius = 500 ] )
```

### Required Arguments

-   **blip**: The blip in which you wish to enable/disable streaming for
-   **streamingEnabled**: A boolean, where *true* enables streaming, and *false* disables it (restoring to previous dimension)

### Optional Arguments

-   **radius:** The maximum distance for players to be within for the blip to be visible. The minimum value is 180 (Radius of the radar itself). Specifying lower will mean the blip only shows when within the radar's visibility.

### Returns

Returns *true* if streaming was enabled/disabled successfully, or *false* if bad arguments were provided

Example
-------

This function makes all vehicles in the server have a streaming blip.

``` lua
function addVehicleBlips()
    for i,vehicle in ipairs(getElementsByType"vehicle") do
        for k,element in ipairs(getAttachedElements(source)) do
            if getElementType(element) == "blip" then
                destroyElement(element)
            end
        end
        --Create a new blip and make it streamable
        local blip = createBlipAttachedTo ( vehicle, 0, 1 )
        call(getResourceFromName"blipstreamer","setBlipStreamable",blip,true,10)
    end
end
addEventHandler ( "onResourceStart", getResourceRootElement(getThisResource()), addVehicleBlips )
```
