This event is triggered when a sound has just finished initial streaming. For file streams, this means the sound will now start playing, but isn't done downloading yet. For live streams, this just means the stream will start playing. This event will also trigger when, for some reason, the streaming failed.

Parameters
----------

``` lua
bool success, int length, string streamName
```

-   **success**: A [boolean](/docs/boolean.md "wikilink") indicating whether the stream was a success or not
-   **length**: The length of the stream in milliseconds. Always returns **0** for a live stream
-   **streamName**: The name of the stream. Note that this isn't the filename. Also note that this isn't always provided

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [sound](/docs/sound.md "wikilink") which either successfully streamed or failed to stream.

Example
-------

This example outputs to the chatbox (if it was a success) “thesoundname has finished in ... milliseconds.”, if it was not a success then it would output “thesoundname failed to start”.

``` lua
addEventHandler("onClientSoundStream",root,function(suc,length,streamN)
    if not suc then outputChatBox("Sound: "..streamN.." failed to start.",100,0,0) return end
    outputChatBox("The sound: "..streamN.." has finished in "..length.."ms.")
end)
```

See Also
--------

### Client player events

### Client event functions
