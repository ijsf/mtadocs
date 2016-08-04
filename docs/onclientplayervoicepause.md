This event is triggered when a player's voice sound is paused using [setSoundPaused](/docs/setsoundpaused.md "wikilink").

Parameters
----------

``` lua
string reason
```

-   **reason**: the reason for the pause, this can be only “paused”.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/Element/Player.md "wikilink") whose voice got paused.

Example
-------

This example outputs nick of whoever's voice is paused.

``` lua
addEventHandler("onClientPlayerVoicePause", root,
    function ()
        outputChatBox(getPlayerName(source) .. "'s voice got paused.")
    end
)
```

See Also
--------

### Client player events

### Client event functions
