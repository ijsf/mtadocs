This event is triggered when any text is output to chatbox, including MTA's hardcoded messages.

Parameters
----------

``` lua
string text, int r, int g, int b
```

-   **text:** The text that was output to chatbox
-   **r:** The amount of red in the color of the text.
-   **g:** The amount of green in the color of the text.
-   **b:** The amount of blue in the color of the text.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the root element.

Cancel effect
-------------

AS OF 1.3.2 If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the game's chat system won't deliver the posts. You may use [outputChatBox](/outputChatBox.md "wikilink") to send the messages then.

Example
-------

This example doesn't output anything to chatbox if it consists only of numbers

    [lua]
    function onClientChatMessageHandler(text)
        if string.match(text,"%d+") --[[/string.match searches for pattern "%d+", means decimals.md|string.match searches for pattern "%d+", means decimals]] == text then -- if string.match and text itself are the same
            cancelEvent() -- don't output it
        end
    end
    addEventHandler("onClientChatMessage", getRootElement(), onClientChatMessageHandler)

See Also
--------

### Client other events

### Client event functions
