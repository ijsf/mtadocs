This event is triggered whenever the local player starts doing a vehicle stunt.

Parameters
----------

``` lua
string stuntType
```

-   **stuntType**: the type of stunt the player is starting to perform. Valid types are:

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the local [player](/player.md "wikilink").

Example
-------

This is a simple stunt script which tells player what stunt he/she started and finished, time the stunt taken to perform and distance travelled while stunting.

``` lua
addEventHandler( "onClientPlayerStuntStart", getRootElement( ),
    function ( stuntType )
        outputChatBox( "You started stunt: " .. stuntType );
    end
);

addEventHandler( "onClientPlayerStuntFinish", getRootElement( ),
    function ( stuntType, stuntTime, distance )
        outputChatBox( "You finished stunt: " .. stuntType ..", Time: " .. tostring( stuntTime ).. ", Distance: " .. tostring( distance ) );
    end
);
```

See Also
--------

### Client player events

### Client event functions
