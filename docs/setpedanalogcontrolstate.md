Sets an analog state of a specified [ped](/docs/ped.md "wikilink")'s control, as if they pressed or released it.

This function only works on [peds](/docs/ped.md "wikilink"), to change the analog control state for a player, please use [setAnalogControlState](/docs/setanalogcontrolstate.md "wikilink").

Syntax
------

``` lua
bool setPedAnalogControlState ( ped thePed, string control, float state ) 
```

### Required Arguments

-   **thePed:** The ped you wish to set the control state of.
-   **control:** The control that you want to set the state of. See [control names](/docs/control_names.md "wikilink") for a list of possible controls.
-   **state:** A float value representing a full analog push ( 1 ) or full release ( 0 ).

### Returns

Returns *true* if the control state was successfully set, *false* otherwise.

Example
-------

This example uses [setPedAnalogControlState](/docs/setpedanalogcontrolstate.md "wikilink") to very slowly accelerate a ped-controlled NRG-500.

``` lua
function createAnalogControlTest ()
    local t_Pos = {getElementPosition(localPlayer)}
    
    local veh = createVehicle (522, unpack(t_Pos))
    local ped = createPed (0, unpack(t_Pos))
    warpPedIntoVehicle (ped, veh)
    
    setPedAnalogControlState (ped, 'accelerate', 0.05)
    setPedAnalogControlState (ped, 'vehicle_left', 1)
end
addCommandHandler ('analogcontroltest', createAnalogControlTest)
```

Requirements
------------

See Also
--------
