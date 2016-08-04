This event gets triggered when nitro state is changing.

Parameters
----------

``` lua
bool state
```

-   **state:** current state of nitro

Source
------

The source of this event is the player vehicle.

Example
-------

This example is showing short chat message on nitro state changing.

<section name="Client" class="client" show="true">
``` lua
function nitro_updateState(state)    
    if state then
        outputChatBox("Nitro #00FF00activated!", 255, 200, 0, true)
    elseif not state then
        outputChatBox("Nitro #FF0000deactivated!", 255, 200, 0, true)
    end
end   
addEventHandler("onClientVehicleNitroStateChange", root,  nitro_updateState)
```

</section>
See Also
--------

### Client vehicle events

### Client event functions
