<div style="border: 1px dotted blue; background: #00CC66;padding:4px;margin-bottom:2px;">
**Note**: This event should only be used as a low-level function for advanced users. For typical Voice scripting, please see the [Voice Resource](/Resource:Voice.md "wikilink")

</div>
This event is triggered when a player starts talking through voice chat.

Parameters
----------

No parameters.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the player [element](/element.md "wikilink") that just started talking through voice chat.

Cancel effect
-------------

If this event is canceled the player will not broadcast his voice chat to anyone in the server.

Example
-------

This example shows how to forbid use voice for not logged in players

``` lua
addEventHandler( 'onPlayerVoiceStart', root,
    function()
        -- if player is not logged in
        -- do not broadcast his voice to other players
        if isGuestAccount( getPlayerAccount(source) ) then
            cancelEvent()
        end
    end
)
```
