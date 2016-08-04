This function sets the heard radio channel, even while not in a vehicle.

Syntax
------

``` lua
bool setRadioChannel ( int ID )             
```

### Required Arguments

-   **ID:** The ID of the radio station you want to play.

### Returns

Returns *true* if channel was set successfully, *false* otherwise.

Example
-------

This example adds a command *setradio* which can be used to change the current radio station by ID.

<section name="Client" class="client" show="true">
``` lua
addCommandHandler ( "setradio",
    function ( command, stationID )
        local result = setRadioChannel ( tonumber( stationID ) )
        if result then -- if we had a valid ID
            outputChatBox ( "Changed your radio station to " .. getRadioChannelName ( tonumber ( stationID ) ) .. "!" )
        else
            outputChatBox ( "Invalid radio station ID, valid ones are 0-12." )
        end
    end
)
```

</section>
Issues
------

See Also
--------

[AR:setRadioChannel](/docs/ar-setradiochannel.md "wikilink")
