This event is triggered every time an explosion is created on the current clients scene (inside the streamer)

Parameters
----------

``` lua
float x, float y, float z, int theType
```

-   **x:** the X Coordinate of where the explosion was created
-   **y:** the Y Coordinate of where the explosion was created
-   **z:** the z Coordinate of where the explosion was created
-   **theType:** the type of explosion created, Values are:

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the explosions creator element (object/vehicle/player)

### Canceling

If this event is [canceled](/docs/Event_system_#Canceling.md "wikilink"), the explosion will not occur.

Example
-------

This example outputs the type of element that created the explosion into the chatbox.

``` lua
function ClientExplosionFunction(x,y,z,theType)
    outputChatBox("Explosion created by a "..getElementType(source))
end
addEventHandler("onClientExplosion",getRootElement(),ClientExplosionFunction)
```

See Also
--------

### Other client events

### Client event functions
