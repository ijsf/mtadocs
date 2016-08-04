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

``` lua
function nickChangeHandler(oldNick, newNick)
outputChatBox(oldNick.." is now known as "..newNick, getRootElement(), 255, 100, 100) -- display the message
end
addEventHandler("onClientChangeNick", getRootElement(), nickChangeHandler) -- add an event handler
```
