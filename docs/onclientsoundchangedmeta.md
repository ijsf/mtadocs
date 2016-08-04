This event is triggered when a sound's meta tags have been modified.

Parameters
----------

``` lua
string streamTitle
```

-   **streamTitle**: The title of a specific stream

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [sound](/sound.md "wikilink") of which the meta tags have just been modified.

Example
-------

<section name="Client" class="client" show="true">
This example will output the new stream title in the chatbox.

``` lua
addEventHandler("onClientSoundChangedMeta", root, function(streamTitle)
    outputChatBox("* Now streaming: "..streamTitle, 255, 200, 0, false)
end)
```

</section>
See Also
--------
