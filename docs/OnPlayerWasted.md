This event is triggered when a player is killed or dies.

Parameters
----------

-   **totalAmmo**: an integer representing the total ammo the victim had when he died.
-   **killer**: an [element](/docs/element.md "wikilink") representing the player or vehicle who was the killer. If there was no killer this is *false*.
-   **killerWeapon**: an integer representing the [killer weapon](/docs/Weapons.md "wikilink") or the [death reason](/Death_Reasons.md "wikilink").
-   **bodypart**: an integer representing the bodypart ID the victim was hit on when he died.

-   

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that died or got killed.

Example
-------

This example prints the killer and bodypart to the chat when a player dies.

``` lua
-- register player_Wasted as a handler for onPlayerWasted
function player_Wasted ( ammo, attacker, weapon, bodypart )
    -- if there was an attacker
    if ( attacker ) then
        -- we declare our variable outside the following checks
        local tempString
        -- if the element that killed him was a player,
        if ( getElementType ( attacker ) == "player" ) then
            -- put the attacker, victim and weapon info in the string
            tempString = getPlayerName ( attacker ).." killed "..getPlayerName ( source ).." ("..getWeaponNameFromID ( weapon )..")"
        -- else, if it was a vehicle,
        elseif ( getElementType ( attacker ) == "vehicle" ) then
            -- we'll get the name from the attacker vehicle's driver
            tempString = getPlayerName ( getVehicleController ( attacker ) ).." killed "..getPlayerName ( source ).." ("..getWeaponNameFromID ( weapon )..")"
        end
        -- if the victim was shot in the head, append a special message
        if ( bodypart == 9 ) then
            tempString = tempString.." (HEADSHOT!)"
        -- else, just append the bodypart name
        else
            tempString = tempString.." ("..getBodyPartName ( bodypart )..")"
        end
        -- display the message
        outputChatBox ( tempString )
    -- if there was no attacker,
    else
        -- output a death message without attacker info
        outputChatBox ( getPlayerName ( source ).." died. ("..getWeaponNameFromID ( weapon )..") ("..getBodyPartName ( bodypart )..")" )
    end
end
addEventHandler ( "onPlayerWasted", getRootElement(), player_Wasted )
```

And another example, this will spawn you in the middle of GTA SA world (x=0, y=0, z=3) after 2 seconds of your death

``` lua
addEventHandler( "onPlayerWasted", getRootElement( ),
    function()
        setTimer( spawnPlayer, 2000, 1, source, 0, 0, 3 )
    end
)
```
