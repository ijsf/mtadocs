This event is triggered when a [player](/docs/player.md "wikilink") joins a server. It is triggered for all players except the local player, as the local player joins the server before their client-side resources are started. It would also be possible for two players to join within a few seconds of each other and for the two players' scripts may not receive onClientPlayerJoin events as their scripts wouldn't have started yet.

Parameters
----------

*None*

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that joined the server.

Example
-------

``` lua
function remotePlayerJoin()
    outputChatBox("* " .. getPlayerName(source) .. " has joined the server")
end
addEventHandler("onClientPlayerJoin", getRootElement(), remotePlayerJoin)
```

See Also
--------

### Client player events

### Client event functions
