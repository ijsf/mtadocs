This function removes a command handler, that is one that has been added using [addCommandHandler](/docs/addcommandhandler.md "wikilink"). This function can only remove command handlers that were added by the resource that it is called in.

Syntax
------

``` lua
bool removeCommandHandler ( string commandName [, function handler] )              
```

### Required Arguments

-   **commandName:** the name of the command you wish to remove.

### Optional Arguments

-   **handler:** the specific handler function to remove. If not specified, all handler functions for the command (from the calling resource) will be removed. *This argument is only available in the server.*

### Returns

Returns *true* if the command handler was removed successfully, *false* if the command doesn't exist.

Example
-------

<section name="Server" class="server" show="true">
This example adds a command handler that briefly shows the position of 'huntedPlayer', and removes the command handler when 'huntedPlayer' dies:

``` lua
-- add a command that allows players to see the position of the 'huntedPlayer' for 5 seconds:
function consoleShowHuntedBlip ( thePlayer, commandName )
    local x, y, z = getElementPosition ( huntedPlayer )
    local huntedblip = createBlip ( x, y, z, 0, 2, 255, 0, 0, 255, thePlayer )
    setTimer ( "destroyElement", 5000, 1, huntedblip )
end
addCommandHandler ( "showhuntedblip", consoleShowHuntedBlip )

-- remove the command once the hunter player dies:
function onHuntedPlayerWasted ( ammo, killer, killerweapon, bodypart )
    removeCommandHandler ( "showhuntedblip" )
end
addEventHandler ( "onPlayerWasted", huntedPlayer, onHuntedPlayerWasted )
```

</section>
<section name="Client" class="client" show="true">
This example adds a command handler that briefly shows the position of 'huntedPlayer', and removes the command handler when 'huntedPlayer' dies:

``` lua
-- add a command that allows players to see the position of the 'huntedPlayer' for 5 seconds:
function consoleShowHuntedBlip ( commandName )
    local x, y, z = getElementPosition ( huntedPlayer )
    local huntedblip = createBlip ( x, y, z, 0, 2, 255, 0, 0, 255, thePlayer )
    setTimer ( "destroyElement", 5000, 1, huntedblip )
end
addCommandHandler ( "showhuntedblip", consoleShowHuntedBlip )

-- remove the command once the hunter player dies:
function onHuntedPlayerWasted ( killer, killerweapon, bodypart )
    removeCommandHandler ( "showhuntedblip" )
end
addEventHandler ( "onClientPlayerWasted", huntedPlayer, onHuntedPlayerWasted )
```

</section>
See Also
--------
