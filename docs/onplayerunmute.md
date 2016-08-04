This event is triggered when a player has been unmuted by [setPlayerMuted](/docs/setPlayerMuted.md "wikilink").

Parameters
----------

*none*

Source
------

The source of this event is the player who got unmuted.

Cancel effect
-------------

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the player will not be unmuted.

Example
-------

This example outputs to chatbox the player name who's unmuted.

``` lua
function unmuted()
    outputChatBox(getPlayerName(source) .. " has been unmuted", root, 255, 0, 0)
end
addEventHandler("onPlayerUnmute", root, unmuted)
```
