This function clears any settings added by setElementVisibleTo and restores an element to its default visibility. This does not work with all entities - [vehicles](/docs/vehicle.md "wikilink"), [players](/player.md "wikilink") and [objects](/object.md "wikilink") are exempt. This is because these objects are required for accurate sync (they're physical objects). This function is particularily useful for changing the visibility of markers, radar blips and radar areas.

Syntax
------

``` lua
bool clearElementVisibleTo ( element theElement )   
```

### Required Arguments

-   **theElement:** The element in which you wish to restore to its default visibility

### Returns

Returns *true* if the operation was successful, *false* otherwise.

Example
-------

This example clears any visibility settings after a player dies, so everyone can see his blip for a short period

``` lua
-- specify the getBlipAttachedTo function
function getBlipAttachedTo( thePlayer )
    local blips = getElementsByType( "blip" )
    for k, theBlip in ipairs( blips ) do
        if getElementAttachedTo( theBlip ) == thePlayer then
            return theBlip
        end
    end
    return false
end

function clearVisibilityWasted ( totalammo, killer, killerweapon, bodypart ) -- when a player dies
    clearElementVisibleTo ( getBlipAttachedTo ( source ) ) -- clear any visiblity settings of his blip
end
addEventHandler ( "onPlayerWasted", getRootElement(), clearVisibilityWasted  ) --add an event handler for onPlayerWasted
```

See Also
--------
