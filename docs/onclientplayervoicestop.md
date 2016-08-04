<div style="border: 1px dotted blue; background: #00CC66;padding:4px;margin-bottom:2px;">
**Note**: This event should only be used as a low-level function for advanced users. For typical Voice scripting, please see the [Voice Resource](/docs/resource-voice.md "wikilink")

</div>
This event is triggered when a player stops talking through voice chat.

Parameters
----------

No parameters.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the player [element](/docs/element.md "wikilink") that just stopped talking through voice chat.

Cancel effect
-------------

-   If the [source](/docs/event_system#event_source.md "wikilink") is the local player, the local player will not broadcast his voice chat to the server
-   If the [source](/docs/event_system#event_source.md "wikilink") is a remote player, the player who started talking will not be heard.

Example
-------

This example outputs to the console the player that stopped talking.

``` lua
addEventHandler("onClientPlayerVoiceStop",root,function()
    outputConsole(getPlayerName(source)..." has stopped talking.")
end)
```

See Also
--------
