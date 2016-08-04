This function sets the rain level to any weather available in GTA. Use [resetRainLevel](/docs/resetrainlevel.md "wikilink") to undo the changes.

Syntax
------

``` lua
bool setRainLevel ( float level )
```

### Required Arguments

-   **level:** A floating point number representing the rain level. 1 represents the maximum rain level usually available in GTA, but higher values are accepted.

### Returns

Returns *true* if the rain level was set, *false* otherwise.

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
