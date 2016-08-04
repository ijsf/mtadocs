This event is triggered when a player has been muted by [setPlayerMuted](/docs/setPlayerMuted.md "wikilink").

Parameters
----------

*none*

Source
------

The source of this event is the player who got muted.

Cancel effect
-------------

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the player will not be muted.

Example
-------

``` lua
function muted()
    outputChatBox(getPlayerName(source) .. " has been muted.", root, 255, 0, 0)
end
addEventHandler("onPlayerMute", root, muted)
```
