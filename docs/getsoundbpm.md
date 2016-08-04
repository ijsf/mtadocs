Syntax
------

``` lua
int getSoundBPM ( element sound )
```

### Required Arguments

-   **sound:** a sound element that is created using [playSound](/docs/playsound.md "wikilink") or [playSound3D](/docs/playsound3d.md "wikilink")

### Returns

Returns the beats per minute of the given sound.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function bpm ()
    -- Long version (might be more understandable as example)
    sound = playSound ( "song.mp3" ) -- Play the song
    beats = getSoundBPM ( sound ) -- Get the beats per minute of the song
    outputChatBox ( "Long code version: " .. beats ) -- Output the beats to the chat box

    -- Short version + Would save some memory
    outputChatBox ( "Short code version: " .. getSoundBPM ( playSound ( "song.mp3" ) ) )
end
addCommandHandler ( "bpm", bpm )
```

</section>
Requirements
------------

See Also
--------

[ar:getSoundBPM](/docs/ar:getsoundbpm.md "wikilink")
