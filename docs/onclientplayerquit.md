This event is triggered when a **remote** player quits the game or leaves the server. It **will not** get triggered on the source player's client. (Use [onClientResourceStop](/docs/onClientResourceStop.md "wikilink") to save client side data when the local player quits.)

Parameters
----------

``` lua
string reason
```

-   **reason**: A string representing the reason why the player quit.
    -   “Unknown”
    -   “Quit”
    -   “Kicked”
    -   “Banned”
    -   “Bad Connection”
    -   “Timed out”

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that quit the game.

Example
-------

This example prints a message in the chatbox when a remote player leaves the server.

``` lua
function onQuitGame( reason )
    outputChatBox ( getPlayerName( source ).." has left the server ("..reason..")" )
end
addEventHandler( "onClientPlayerQuit", getRootElement(), onQuitGame )
```

See Also
--------

### Client player events

### Client event functions
