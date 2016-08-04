This event is triggered when a player changes his nickname.

Parameters
----------

``` lua
string oldNick, string newNick, bool changedByUser
```

-   **oldNick:** the nickname the player had before.
-   **newNick:** the new nickname of the player.

Source
------

The source of this event is the player that changed his nick

Cancel effect
-------------

Cancelling this event depends on how it is called, if it is called by the scripting event then it is NOT cancelable. If it is called from the /nick command it IS cancelable. If this event is cancelled and can be cancelled then the name will not change.

Example
-------

``` lua
function nickChangeHandler(oldNick, newNick)
    -- check if there's account with newNick as username
    if getAccount(newNick) then
        outputChatBox("Sorry, there already exists an account with your new nickname as username.", source, 0, 255, 0)
        outputChatBox("Please choose another one.", source, 0, 255, 0)
        -- cancel the event to prevent the nick from being changed
        cancelEvent()
    end
end
-- add an event handler
addEventHandler("onPlayerChangeNick", getRootElement(), nickChangeHandler)
```

This example displays a message to everyone every time player changed his nick

``` lua
function nickChangeHandler(oldNick, newNick)
outputChatBox(oldNick.." is now known as "..newNick, getRootElement(), 255, 100, 100) -- display the message
end
addEventHandler("onPlayerChangeNick", getRootElement(), nickChangeHandler) -- add an event handler
```

Issues
------
