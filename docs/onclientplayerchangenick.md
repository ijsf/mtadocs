This event is triggered when a player changes his nickname.

Parameters
----------

``` lua
string oldNick, string newNick
```

-   **oldNick:** the nickname the player had before.
-   **newNick:** the new nickname of the player.

Source
------

The source of this event is the player that changed his nick

Example
-------

This example snippet sends a lame message every time the local player changes his nick.

``` lua
addEventHandler ( "onClientPlayerChangeNick", getLocalPlayer(),
    function ( oldNick, newNick )
        outputChatBox ( "Hi " .. oldNick .. "! Oh... You're not " .. oldNick .. " anymore, are you?", 0, 255, 0 )
        outputChatBox ( "I like your new name, " .. newNick .. "!", 0, 255, 0 )
    end
)
```

See Also
--------

### Client player events

### Client event functions
