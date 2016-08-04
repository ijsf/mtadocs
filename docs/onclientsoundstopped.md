Parameters
----------

``` lua
string reason
```

-   **reason**: the reason the **sound** was stopped, can be “finished”, “paused” or “destroyed”.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [sound's element](/Element/Sound.md "wikilink").

Example
-------

This example outputs the reason the sound stopped.

``` lua
function onSoundStopped ( reason )
    if ( reason == "destroyed" ) then
        outputChatBox ( "sound destroyed" )
    elseif ( reason == "finished" ) then
        outputChatBox ( "end of sound" )
    elseif ( reason == "paused" ) then
        outputChatBox ( "sound paused" )
    end
end
addEventHandler ( "onClientSoundStopped", getRootElement(), onSoundStopped )
```

See Also
--------

### Client sound events

### Client event functions
