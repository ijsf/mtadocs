Parameters
----------

``` lua
string fileName, bool success
```

-   **fileName**: the file downloaded.
-   **success**: whether successful or not.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [root element](/root_element.md "wikilink") of the resource that called [downloadFile](/downloadFile.md "wikilink").

Example
-------

This example plays a sound if it was downloaded successfully

``` lua
function onDownloadFinish ( file, success )
    if ( source == resourceRoot ) then                            -- if the file relates to this resource
        if ( success ) then                                       -- if the file was downloaded successfully
            if ( file == "test.mp3" ) then                        -- if the file name is what we were expecting
                currentTrack = playSound ( "test.mp3" )
            end
        else                                                      -- if the file wasn't downloaded successfully
            if ( file == "test.mp3" ) then
                outputChatBox ( "test.mp3 failed to download" )
            end
        end
    end
end
addEventHandler ( "onClientFileDownloadComplete", root, onDownloadFinish )
```

See Also
--------

### Other client events

### Client event functions
