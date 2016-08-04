Syntax
------

``` lua
bool isElementWaitingForGroundToLoad ( element theElement )
```

### Required arguments

-   **theElement:** the element to check its frozen waiting for custom map objects to load status. It can be a [vehicle](/docs/vehicle.md "wikilink"), [ped](/ped.md "wikilink") or [player](/player.md "wikilink").

### Returns

Returns *true* if the specified [element](/docs/element.md "wikilink") is frozen waiting for collisions of custom map objects to load. Returns *false* if it's not or if the specified [element](/element.md "wikilink") is invalid.

Example
-------

<section name="Serverside example" class="server" show="true">
The next code snippet outputs a message when a vehicle respawns far away from players, above an [object](/docs/object.md "wikilink").

``` lua
local function notifyFarRespawnOnMap()
    if isElementWaitingForGroundToLoad(source) then
        outputChatBox("* A " .. getVehicleName(source) .. " respawned above an object which is far away! Find it quick!", root, 128, 255, 0)
    end
end
addEventHandler("onVehicleRespawn", root, notifyFarRespawnOnMap)
```

</section>
See also
--------
