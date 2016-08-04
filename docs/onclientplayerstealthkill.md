This event is triggered when the local player stealth kills another player.

Parameters
----------

``` lua
element targetPlayer
```

-   **targetPlayer**: The [player](/docs/player.md "wikilink") or [ped](/ped.md "wikilink") that is being stealth killed.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that initiated the stealth kill. (Local player only)

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), then the stealth kill is aborted.

Example
-------

This example disables stealth kills.

``` lua
function abortAllStealthKills(targetPlayer)
    cancelEvent()
end
addEventHandler("onClientPlayerStealthKill", getLocalPlayer(), abortAllStealthKills)
```

See Also
--------

### Client player events

### Client event functions
