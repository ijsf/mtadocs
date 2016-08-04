This event is triggered when a player sends a private message with *msg* command.

Parameters
----------

``` lua
string message, player recipient
```

-   **message**: A string representing the private message typed.
-   **recipient**: The [player](/docs/player.md "wikilink") to whom the message is being sent.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") who sent the private message.

Cancel effect
-------------

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the game's chat system won't deliver the message. You may use [outputChatBox](/outputChatBox.md "wikilink") to send the messages then.

Example
-------

This example blocks players sending a PM to a player named “Bob”.

``` lua
function blockPM(msg,r)
    if (getPlayerName(r) == "Bob") then -- If they sent a PM to "Bob"
        cancelEvent() -- Then cancel it
        outputChatBox("Bob is not accepting PM's at this time.",source,255,0,0) -- And output it was cancelled.
    end
end
addEventHandler("onPlayerPrivateMessage",getRootElement(),blockPM)
```
