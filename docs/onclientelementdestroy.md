This event is triggered when an element gets destroyed by [destroyElement](/docs/destroyelement.md "wikilink") or when the creator resource is stopping. It is also triggered when a parent element of this element is destroyed.

Parameters
----------

*None*

Source
------

The source of this event is the element that is being destroyed.

Example
-------

This example prints a message in the chat box when the vehicle that you are in gets destroyed.

``` lua
addEventHandler("onClientElementDestroy", getRootElement(), function ()
    if getElementType(source) == "vehicle" and getPedOccupiedVehicle(getLocalPlayer()) == source then
        outputChatBox("The vehicle that you were in has been destroyed by the script")
    end
end)
```

[pl:onClientElementDestroy](/docs/pl-onclientelementdestroy.md "wikilink")

See Also
--------

### Client element events

### Client event functions
