This event is triggered when a player disconnects from the server.

Parameters
----------

``` lua
string quitType, string reason, element responsibleElement
```

-   **quitType**: How the player left.

This argument can be:

-   “Unknown”
-   “Quit”
-   “Kicked”
-   “Banned”
-   “Bad Connection”
-   “Timed out”

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that left the server.

Example
-------

This example gets the quitting client's name and outputs that he is gone

``` lua
-- we register quitPlayer as a handler for the event
function quitPlayer ( quitType )
    -- send the message to the server telling players that the player has left.
    outputChatBox ( getPlayerName(source).. " has left the server (" .. quitType .. ")" )
end
addEventHandler ( "onPlayerQuit", getRootElement(), quitPlayer )
```
