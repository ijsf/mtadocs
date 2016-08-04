This function retrieves [element data](/element_data.md "wikilink") attached to an element under a certain key.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **theElement:** This is the element with data you want to retrieve.
-   **key:** The name of the element data entry you want to retrieve. (Maximum 31 characters.)

### Optional Arguments

-   **inherit:** - toggles whether or not the function should go up the hierarchy to find the requested key in case the specified element doesn't have it.

### Returns

This function returns a *variable* containing the requested element data, or *false* if the element or the element data does not exist. When getting data corresponding to a XML attribute, this is always a *string*.

Example
-------

This example stores the tick count when a player joins and then allows players to see how long they are connected using a console function 'joinTime'.

<section show="true" name="Server" class="server">
``` lua
function joinTime ( )
    setElementData ( source, "joinTime", getTickCount() ) -- Store the current tick count in the player's data with the key 'joinTime'
end
-- Make our 'joinTime' function be called when a player joins
addEventHandler ( "onPlayerJoin", root, joinTime )

function showJoinTime ( source, commandName, playerName )
    if ( playerName ) then -- see if a player was specified
        thePlayer = getPlayerFromName ( playerName ) -- get the player element for the specified player
        if ( thePlayer ) then -- if one was found...
            local timeOnline = (getTickCount() - getElementData ( thePlayer, "joinTime" )) / 1000 -- calculates the time since join
            outputChatBox ( getPlayerName ( thePlayer ).." joined "..timeOnline.." seconds ago", source ) -- output the player's join time
        else
            outputChatBox ( "Couldn't find '" .. playerName .. "'", source ) -- display an error
        end
    else
        -- display when the player who used the function joined and inform how to see other people's join time
        local timeOnline = (getTickCount() - getElementData ( source, "joinTime" )) / 1000 -- calculate the time since join
        outputChatBox ( "You joined " ..timeOnline.." seconds ago", source )
        outputChatBox ( "Use 'join_time <player name>' to see other people's join time", source )
    end
end
-- Add a console command joinTime, that takes an optional parameter of a player's name
addCommandHandler ( "joinTime", showJoinTime )
```

</section>
See Also
--------
