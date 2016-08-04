This event is triggered whenever a physical element is streamed in. This is triggered for all elements that are streamable, such as players, peds, vehicles, objects and markers. When this event is triggered, that element is guaranteed to be physically created as a GTA object.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [element](/element.md "wikilink") that streamed in

Example
-------

This example shows you how to tell player that a marker was streamed in and the distance between player and the marker.

``` lua
addEventHandler( "onClientElementStreamIn", getRootElement( ),
    function ( )
        if getElementType( source ) == "marker" then
            local myPosTab = { getElementPosition( getLocalPlayer( ) ) };
            local markerPosTab = { getElementPosition( source ) };
            local distance = getDistanceBetweenPoints3D( unpack( myPosTab ), unpack( markerPosTab ) );
            outputChatBox( "A marker has just streamed in. Distance to the marker: " .. tostring( distance ) .."." );
        end
    end
);
```

See Also
--------

### Client element events

### Client event functions
