This function stores [element data](/docs/element_data.md "wikilink") under a certain key, attached to an element. Element data set using this is then synced with all clients and the server. The data can contain server created elements, but you should avoid passing data that is not able to be synced such as xmlnodes, acls, aclgroups etc.

As element data is synced to all clients, it can generate a lot of network traffic and consume server CPU. Events are much more efficient for sending data from a client to the server only, or from the server to a specific client.

Syntax
------

``` lua
bool setElementData ( element theElement, string key, var value [, bool synchronize = true ] )
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") you wish to attach the data to.
-   **key:** The key you wish to store the data under. (Maximum 31 characters.)
-   **value:** The value you wish to store. See [element data](/docs/element_data.md "wikilink") for a list of acceptable datatypes.

### Optional Arguments

-   **synchronize:** Determines whether or not the data will be synchronized with the server (client-side variation) and remote clients (both variations).

### Returns

Returns *true* if the data was set succesfully, *false* otherwise.

### Issues

Example
-------

<section name="Server" class="server" show="true">
This example allows a player to add a custom tag onto their nickname, and also reverts it back to normal if they wish.

``` lua
function addPlayerCustomTag ( thePlayer, command, newTag )
    --Let's make sure the newTag param has been entered...
    if ( newTag ) then
        --Grab their current playername for saving.
        local sPlayerNickname = getPlayerName ( thePlayer )
        --Create their new nickname with their tag
        local sNewPlayerNickname = newTag .. " " .. sPlayerNickname
        
        --Let's first load the element data, see if it's there already
        --The reason for this is that if a player were to do /addtag twice,
        --the tag would be prepended a second time
        local sOldNick = getElementData( thePlayer, "tempdata.originalnick" )
        if ( sOldNick == false ) then
            --Save their orignal nickname in their element data
            setElementData ( thePlayer, "tempdata.originalnick", sPlayerNickname )
        end
        
        --Set their new nickname globally
        setPlayerName ( thePlayer, sNewPlayerNickname )
        
        --Tell them it's done
        outputChatBox ( "Your new nickname has been set, to put it back to its original state you can use /deltag", thePlayer )
    else
        --The newTag param was not entered, give an error message
        outputChatBox ( "/addtag - Incorrect syntax, Correct: /addtag <newtag>", thePlayer )
    end
end
addCommandHandler ( "addtag", addPlayerCustomTag )

function removePlayerCustomTag ( thePlayer, command )
    --We first need to check that they have already used /addtag, let's do that now
    local sOldNick = getElementData( thePlayer, "tempdata.originalnick" )
    if ( sOldNick ) then
        --Great, they have a tag added, let's reset them
        
        --First we will want to reset the element data back to its default (that being false)
        setElementData ( thePlayer, "tempdata.originalnick", false )
        
        --Now set the client name back
        setPlayerName( thePlayer, sOldNick )
        
        --Notify them
        outputChatBox ( "Your old nickname has been set", thePlayer )
    end
end
addCommandHandler ( "deltag", removePlayerCustomTag )
```

</section>
See Also
--------
