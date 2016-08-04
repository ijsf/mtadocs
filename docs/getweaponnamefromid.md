This function allows you to retrieve the name of a weapon from an ID. Note it also allows you to retrieve the name of other methods of death, such as *Fall* and *Rammed*.

Syntax
------

``` lua
string getWeaponNameFromID ( int id )            
```

### Required Arguments

-   **id:** The ID you wish to retrieve the name of

### Returns

Returns a string of the name of the weapon, *false* otherwise. Names will be like these: (Ignoring case)

Example
-------

<section name="Server" class="server" show="true">
This example displays a death message in the format of "\* *Killer* killed *dead* (*Weapon*)"

``` lua
function scriptOnPlayerWasted ( totalammo, killer, killerweapon, bodypart ) --when a player dies
    local causeOfDeath = getWeaponNameFromID ( killerweapon ) --get the name of 'killerweapon' and define it as 'causeOfDeath'
    local killedPerson = getPlayerName ( source ) --get the name of the player who died and define it as 'killedPerson'
    if ( killer ) then --if there was a killer
    local killerPerson = getPlayerName ( killer ) --get the name of the killer and define it as 'killerPerson'
        if ( killer == source ) then --if the killer is the same as the person who died i.e. he killed himself
            outputChatBox ( "* "..killerPerson.." died ("..causeOfDeath..")", getRootElement(), 255, 100, 100 ) --output in the chatbox that  he died and the method he died in the brackets
        else --if the killer is not the same as the person who died
            outputChatBox ( "* "..killerPerson.." killed "..killedPerson.." ("..causeOfDeath..")", getRootElement(), 255, 100, 100 ) --output in the chatbox that he was killed by the killer and the method in brackets
        end
    else --if there was no killer
        outputChatBox ( "* "..killedPerson .. " died (" ..causeOfDeath..")", getRootElement(), 255, 100, 100 ) --output in the chatbox that the person died and how he died
    end
end
addEventHandler ( "onPlayerWasted", getRootElement(), scriptOnPlayerWasted ) --add an event handler for onPlayerWasted
```

</section>
Issues
------

See Also
--------

[ru:getWeaponNameFromID](/docs/ru:getweaponnamefromid.md "wikilink")
