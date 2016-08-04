This event is triggered when a sound has just finished downloading. This means the complete sound file is now loaded in the player's RAM, and can be played completely from start to end. Unlike [onClientSoundStream](/docs/onclientsoundstream.md "wikilink"), this event only triggers for file streams, not for live ones since live streams never actually end.

Parameters
----------

``` lua
int length
```

-   **length**: The length of the stream in milliseconds

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [sound](/docs/sound.md "wikilink") which just finished downloading.

Example
-------

This example would output to the chatbox after the sound is finish that the sound has finished downloading in ... milliseconds.

``` lua
addEventHandler("onClientSoundFinishedDownload",root,function(length)
    local meta = getSoundMetaTags(source)
    outputChatBox("The sound: "..(meta.title).." has finished in :"..length.."ms.")
end)
```

See Also
--------

### Client player events

### Client event functions
