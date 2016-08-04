Parameters
----------

``` lua
string reason
```

-   **reason**: the reason the **sound** was started, can be “play” or “resumed”.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [sound's element](/Element/Sound.md "wikilink").

Example
-------

This example outputs the reason the sound started .

``` lua
function onSoundStarted ( reason )
    if ( reason == "play" ) then
        outputChatBox ( "sound started" )
    elseif ( reason == "resumed" ) then
        outputChatBox ( "sound resumed" )
    end
end
addEventHandler ( "onClientSoundStarted", getRootElement(), onSoundStarted )
```

See Also
--------

### Client sound events

### Client event functions