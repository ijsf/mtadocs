This function gets the syncer of an element. The syncer is the player who is in control of the element.

Syntax
------

``` lua
element getElementSyncer ( element theElement )
```

### Required Arguments

-   **theElement**: The [element](/element.md "wikilink") to get the syncer of.

### Returns

Returns the [element](/element.md "wikilink") that is the syncer of *theElement* or *false* if the element does not have a syncer.

Example
-------

This code will kill the syncer of the first ped created with createPed.

``` lua
local elementSyncer = getElementSyncer(getElementsByType("ped")[1])
if elementSyncer and getElementType(elementSyncer) == "player" then --Check if its a player and if there is a syncer
    killPed(elementSyncer, elementSyncer)
end
```

This code will kill the syncer of the ped created with createPed.

``` lua
function test(player,commandName)
    local idlewoodPed = createPed(26,1813.27,-1897.04,13.577)
    local elementSyncer = getElementSyncer(idlewoodPed)
    if elementSyncer and getElementType(elementSyncer) == "player" then --Check if its a player and if there is a syncer
        killPed(elementSyncer, elementSyncer)
    end
end
addCommandHandler("test", test)
```

See Also
--------
