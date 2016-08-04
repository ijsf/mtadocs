This event is triggered when a player stealth kills another player.

Parameters
----------

``` lua
element targetPlayer
```

-   **targetPlayer**: The [player](/docs/player.md "wikilink") or [ped](/ped.md "wikilink") that is being stealth killed.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that initiated the stealth kill.

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), then the stealth kill is aborted.

Example
-------

<section name="Server" class="server" show="true">
    [lua]
    function onStealthKill(targetPlayer)
         outputChatBox("Stealth kill!", source) -- Tell the player he/she has done a stealth kill.
         outputChatBox("" .. getPlayerName(targetPlayer) .. " has been stealth-killed by " .. getPlayerName(source) .. ".")
    end
    addEventHandler("onPlayerStealthKill", getRootElement(), onStealthKill) -- Adds a handler for the stealth kill event.

</section>
<section name="Server" class="server" show="true">
    [lua]
    function onStealthKill(targetPlayer)
         cancelEvent(true, "No more stealth kills.") -- Aborts the stealth-kill.
    end
    addEventHandler("onPlayerStealthKill", getRootElement(), onStealthKill) -- Adds a handler for the stealth kill event.

</section>
