Analogous to [onResourceStart](/onResourceStart.md "wikilink"), but triggered before script files are initialised.

**Important:** If you attach this event to the [root element](/root_element.md "wikilink") it will be called when *any* [resource](/resource.md "wikilink") starts - attach it to to the [root element](/root_element.md "wikilink") of the desired resource, eg. [getResourceRootElement](/getResourceRootElement.md "wikilink")([getResourceFromName](/getResourceFromName.md "wikilink")(“freeroam”)).

Parameters
----------

``` lua
resource startingResource
```

-   **startingResource**: The resource that is starting

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the root [element](/element.md "wikilink") of the resource.

Cancel effect
-------------

If this event is cancelled, the resource won't begin starting.

Example
-------

This code will output the name of any resource that is starting.

``` lua
function displayStartingRes ( res )
    outputChatBox ( "Resource " .. getResourceName(res) .. " is going to start", getRootElement(), 255, 255, 255 )
end
addEventHandler ( "onResourcePreStart", getRootElement(), displayStartingRes )
```
