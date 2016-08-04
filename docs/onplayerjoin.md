This event is triggered when a player joins the server.

Parameters
----------

No parameters.

Source
------

The source of this event is the [player](/docs/player.md "wikilink") who joined.

Example
-------

This example gets the joined client's name and sends him a welcome message including his name.

``` lua
-- we register greetPlayer as a handler for the event
function greetPlayer ( )
    -- we store the player's name
    local joinedPlayerName = getPlayerName ( source )
    local serverName = getServerName( )
    -- and send him a greeting
    outputChatBox ( "Welcome " .. joinedPlayerName .. " to ".. serverName .."!" , source, 255, 255, 255 )
end
addEventHandler ( "onPlayerJoin", getRootElement(), greetPlayer )
```

This example sets random color to every player who joins.

``` lua
-- create a table to save the color
ChatColors = {}

-- sets colors when player join
function onJoin ()
        -- create a table to add rgb values. Index will be the player element
    ChatColors[source] = {math.random (50, 255), math.random (50, 255), math.random (50, 255)}
end
-- checks if player has sent a message
function onChat ( message, messageType )
    if messageType == 0 then
                -- use the table to get the saved rgb values
        outputChatBox ( getPlayerName ( source ) .. ": #E0D0B0" .. message, getRootElement(), ChatColors[source][1], ChatColors[source][2], ChatColors[source][3], true )
        cancelEvent()
    end
end
addEventHandler ( "onPlayerJoin", getRootElement(), onJoin)
addEventHandler ( "onPlayerChat", getRootElement(), onChat )
```
