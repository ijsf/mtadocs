This event is triggered whenever a physical element is streamed out. This is triggered for all elements that are streamable, such as players, peds, vehicles, objects and markers when the local player is leaving the element. When this event is triggered, that element is no longer physical and is now virtualized by MTA.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [element](/element.md "wikilink") that streamed out

Example
-------

This example shows you how to tell player that a marker was streamed out and the distance between player and the marker.

``` lua
addEventHandler( "onClientElementStreamOut", getRootElement( ),
    function ( )
        if getElementType( source ) == "marker" then
            local myPosTab = { getElementPosition( getLocalPlayer( ) ) };
            local markerPosTab = { getElementPosition( source ) };
            local distance = getDistanceBetweenPoints3D( unpack( myPosTab ), unpack( markerPosTab ) );
            outputChatBox( "A marker has just streamed out. Distance to the marker: " .. tostring( distance ) .."." );
        end
    end
);
```

See Also
--------

### Client element events

### Client event functions
