This function sets the health for the specified [element](/docs/element.md "wikilink"). This can be a [ped](/docs/ped.md "wikilink"), [object](/docs/object.md "wikilink") or a [vehicle](/docs/vehicle.md "wikilink").

Syntax
------

``` lua
bool setElementHealth ( element theElement, float newHealth )
```

### Required Arguments

-   **theElement:** The [ped](/docs/ped.md "wikilink"), [vehicle](/docs/vehicle.md "wikilink") or [object](/docs/object.md "wikilink") whose health you want to set.
-   **newHealth:** A float indicating the new health to set for the element.

### Returns

Returns *true* if the new health was set successfully, or *false* if invalid arguments were passed.

Example
-------

<section name="Server" class="server" show="true">
This example adds a 'hpslap' console command that lets players “slap” others (doing 20 damage).

``` lua
function hpSlap ( sourcePlayer, command, targetPlayerName )
    -- check if the user has access to it first
    if not hasObjectPermissionTo(sourcePlayer, "command.slap", false) then
        outputChatBox ( "You cannot use this command.", sourcePlayer )
        return false
    end
    -- look up the player to be slapped
    local targetPlayer = getPlayerFromName ( targetPlayerName )
    -- if there's a player with such name,
    if targetPlayer then
        -- subtract 20 from his health
        setElementHealth ( targetPlayer, getElementHealth(targetPlayer) - 20 )
    else
        -- otherwise, output an error message
        outputChatBox ( "There is no player named " .. targetPlayerName .. "!", sourcePlayer )
    end
end
-- add our function as a handler for "hpslap"
addCommandHandler ( "hpslap", hpSlap )
```

</section>
See Also
--------
