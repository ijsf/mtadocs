This event is triggered when a resource is started.

**Important:** If you attach this event to the root element it will called when *any* resource starts, not just the resource your script is running inside. As such, most of the time you will want to check that the resource passed to this event matches your resource (compare with the value returned by [getThisResource](/docs/getthisresource.md "wikilink")) before doing anything. Alternatively you can attach the event to [getResourceRootElement](/getResourceRootElement.md "wikilink")([getThisResource](/getThisResource.md "wikilink")()).

Parameters
----------

``` lua
resource startedResource
```

-   **startedResource**: The resource that was started

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the root [element](/element.md "wikilink") in the resource that started.

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the resource starting is aborted and is stopped again.

Example
-------

This code will output the name of any resource that is started.

``` lua
function displayLoadedRes ( res )
    outputChatBox ( "Resource " .. getResourceName(res) .. " loaded", getRootElement(), 255, 255, 255 )
end
addEventHandler ( "onResourceStart", getRootElement(), displayLoadedRes )
```
