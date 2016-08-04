<div style="border: 1px dotted blue; background: #00CC66;padding:4px;margin-bottom:2px;">
**Note**: This event should only be used as a low-level function for advanced users. For typical Voice scripting, please see the [Voice Resource](/docs/Resource:Voice.md "wikilink")

</div>
This event is triggered when a player stops talking through voice chat.

Parameters
----------

No parameters.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the player [element](/element.md "wikilink") that just stopped talking through voice chat.

Example
-------

This example outputs to the world that the player stopped talking.

``` lua
addEventHandler("onPlayerVoiceStop",root,function()
    outputChatBox(getPlayerName(source)..." has stopped talking.",root)
end)
```
