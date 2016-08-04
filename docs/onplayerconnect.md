This event is triggered when a player attempts to connect to the server.

Parameters
----------

``` lua
string playerNick, string playerIP, string playerUsername, string playerSerial, int playerVersionNumber, string playerVersionString
```

-   **playerNick**: The player's current nickname.
-   **playerIP**: The player's current IP.
-   **playerUsername**: The player's community username.
-   **playerSerial**: The player's serial number.
-   **playerVersionNumber**: The player's MTA version in pure numerical form, e.g. **'256**' for 1.0, **'257**' for 1.0.1, etc.
-   **playerVersionString**: The player's MTA version in sortable string form. Same as the return value from [getPlayerVersion](/docs/getplayerversion.md "wikilink").

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the client's [root element](/docs/root_element.md "wikilink").

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the player will be disconnected with an error message saying the reason specified in cancelEvent or “Disconnected: server refused the connection” if none was specified.

Example
-------

This example cancels connection attempts of people who use the nick “Player” or outputs some data about the connecting player otherwise.

``` lua
--when a player connects
function playerConnect (playerNick, playerIP, playerUsername, playerSerial, playerVersionNumber)
    if playerNick == "Player" then --check if his nick is "Player"
        cancelEvent(true,"The nick \"Player\" is not allowed, please change it to something else. You can change your nick in Settings menu Multiplayer tab.") --in that case refuse the connection
    else
        --output some data about the player
        outputChatBox (playerNick.." just connected to the server.")
        outputChatBox ("IP: "..playerIP.." Username: "..playerUsername.." Serial: "..playerSerial)
    end
end

--add the playerConnect function as a handler for onPlayerConnect
addEventHandler ("onPlayerConnect", getRootElement(), playerConnect)
```

This example cancels connection if player uses older MTA (older than 1.0.3)

``` lua
addEventHandler( "onPlayerConnect", getRootElement(),
    function ( _,_,_,_, clientVersion )
        if ( clientVersion < 259 ) then
            cancelEvent( true, "Update your MTA before you join this server!" );
        end
    end
)
```
