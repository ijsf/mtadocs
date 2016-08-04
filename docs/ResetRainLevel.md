This function resets the rain level of the current weather to its default.

Syntax
------

``` lua
bool resetRainLevel ( )
```

Returns
-------

Returns true if the rain level was reset.

Example
-------

<section name="Client" class="client" show="true">
This example will make it rain when you enter a vehicle and stop it when you leave the vehicle.

``` lua
function startRaining()
         setRainLevel(5)
end
addEventHandler("onClientVehicleEnter", getRootElement(), startRaining)

function stopRaining()
         resetRainLevel()
end
addEventHandler("onClientVehicleExit", getRootElement(), stopRaining)
```

</section>
See Also
--------
