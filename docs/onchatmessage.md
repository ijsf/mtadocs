This event is triggered when a player uses say, teamsay, me successfully. Or when any message is output to chat using [outputChatBox](/docs/outputchatbox.md "wikilink") on the server side. It can be used to get the resource responsible for specific [outputChatBox](/outputChatBox.md "wikilink") call via the second parameter.

Parameters
----------

``` lua
string theMessage, resource / element theElement
```

-   **theMessage:** The text that was output to the chatbox
-   **theElement:** Player element if chatbox output was done via say, teamsay or me. Resource if it was done via [outputChatBox](/docs/outputchatbox.md "wikilink").

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the root element.

Example
-------

This example outputs all chat messages to debug view.

    [lua]
    function onChatMessageHandler(theMessage, thePlayer)
        outputDebugString(theMessage)
    end
    addEventHandler("onChatMessage", root, onChatMessageHandler)

Requirements
------------
