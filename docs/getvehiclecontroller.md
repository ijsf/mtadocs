This function is used to get the player in control of the specified vehicle which includes somebody who is trying to enter the drivers seat.

Syntax
------

``` lua
player getVehicleController ( vehicle theVehicle )            
```

### Required Arguments

-   **theVehicle:** the [vehicle](/docs/vehicle.md "wikilink") you want to get the 'controller' of.

### Returns

Returns a [player](/docs/player.md "wikilink") object, if there isn't a driver, it will search the 'trailer chain' for the front driver, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example outputs a chatbox message when a vehicle gets a trailer attached.

``` lua
function scriptOnTrailerAttach ( towedBy )
  thePlayer = getVehicleController ( source ) -- get the controller of the towing vehicle
  if ( thePlayer ) then
    outputChatBox ( getPlayerName ( thePlayer ).. " attached a trailer" )
  else
    outputChatBox ( "trailer attached" )
  end
end
addEventHandler ( "onTrailerAttach", getRootElement(), scriptOnTrailerAttach )
```

</section>
See Also
--------
