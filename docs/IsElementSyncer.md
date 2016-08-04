This function checks whether an [element](/element.md "wikilink") is synced by the local player or not. Accepted elements are [peds](/ped.md "wikilink") and [vehicles](/vehicle.md "wikilink").

Syntax
------

``` lua
bool isElementSyncer ( element theElement )
```

### Required Arguments

-   **theElement**: The [element](/element.md "wikilink") to check.

### Returns

Returns *true* if the passed element is synced by the local player, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example draws a string above peds synced by local player in 50m proximity

``` lua
function renderSyncedElements ()
    -- Retrieve ped elements streamed in
    for k,el in ipairs (getElementsByType('ped', root, true)) do
        repeat
            if (not isElementSyncer(el)) then
                -- Skip if local player isn't syncer
                break
            end
            
            local pedX, pedY, pedZ = getElementPosition (el)
            local sX, sY, sD = getScreenFromWorldPosition (pedX, pedY, pedZ + 1.2)
            if (not sX) or (sD > 50) then
                -- Not on screen or too far away
                break
            end
            
            dxDrawText ('Syncer', sX, sY, 0, 0, tocolor(255,255,255,255), 20 / sD, 'arial')
        until true
    end
end
addEventHandler ('onClientRender', root, renderSyncedElements)
```

</section>
See Also
--------
