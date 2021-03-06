This function changes the specified [client](/docs/client.md "wikilink")'s name.

Syntax
------

``` lua
bool setClientName ( client theClient, string newName )
```

### Required Arguments

-   **theClient:** the [client](/docs/client.md "wikilink") that will have its name set.
-   **newName:** the new name to set for the client.

### Returns

Returns *true* if the client's name was changed succesfully, *false* if invalid arguments are specified.

Example
-------

<section name="Server" class="server" show="true">
This example adds a tag before a player's nickname via a /changetag command

``` lua

--Define the function for this command (/changetag, as defined below)
--Source = the player that triggered this command
--Command = The command passed into the function (changetag)
--thePlayer = The player argument that you wish to add a tag too
--tag = The tag to add to the players nickname
function tagPlayer( source, command, thePlayer, tag )
    --Attempt to grab the elemennt id for the player from the parsed name.
    local sPlayerElement = getPlayerFromNick(thePlayer)
    --Check to see if the player were changing the tag for exists.
    if (sPlayerElement) then
        --make sure that the element type of thePlayer is acctually pointing to a player element
        if getElementType( sPlayerElement ) == "player" then
            --we store the player's current name,
            local oldName = getClientName( sPlayerElement )
            --append the tag passed to this function before it
            local taggedName = tag .. oldName
            --then set it as his new name
            setClientName( sPlayerElement, taggedName )
            --Tell the player who triggerd the command that the tag has been applied
            outputChatBox ( "Player " .. thePlayer .. "'s tag changed to " .. taggedName, source )
        end
    else
        --Tell the player who triggerd the command that the player could not be found
        outputChatBox ( "Unable to change player tag: Player " .. thePlayer .. " not found", source )
    end
end
--Add a command handler for either the console or / chat commands
--Example: /changetag <playername> <tag>
addCommandHandler ( "changetag", tagPlayer )
```

</section>
See Also
--------
