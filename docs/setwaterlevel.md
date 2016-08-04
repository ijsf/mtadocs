Sets the height of some or all the water in the game world.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setWaterLevel ( [water theWater,] float level )
```

``` lua
bool setWaterLevel ( float level [, bool includeWaterFeatures = true, bool includeWaterElements = true ] )
```

### Required Arguments

-   **level:** the new Z coordinate of the water surface. All water in the game world is set to this height.

### Optional Arguments

-   **theWater:** the water element to change.

*or:*

### Returns

Returns *true* if successful, *false* in case of failure.

</section>
<section name="Client" class="client" show="true">
``` lua
 float level )
bool setWaterLevel ( [water theWater,] float level )
bool setWaterLevel ( float level [, bool includeWaterFeatures = true, bool includeWaterElements = true ] )
```

### Required Arguments

-   **level:** the new Z coordinate of the water surface. If **x**, **y** and **z**, or **water**, are specified, the area of water containing that point or corresponding to that water element is changed. Otherwise, all water in the game world is changed.

### Optional Arguments

-   **x:** the X coordinate of the point indicating the water area to change.
-   **y:** the Y coordinate of the point indicating the water area to change.
-   **z:** the Z coordinate of the point indicating the water area to change. This parameter is reserved and is currently ignored, set it to 0.

*or:*

-   **theWater:** the water element to change.

*or:*

### Returns

Returns *true* if successful, *false* in case of failure (there is no water at the specified coordinates).

</section>
Example
-------

<section name="Client" class="client" show="true">
This example code will slowly drain away all rivers and seas.

``` lua
local level = 0

function drainSomeWater()
    level = level - 0.01
    setWaterLevel ( level )
end
setTimer ( drainSomeWater, 100, 15000 )
```

</section>
<section name="Server" class="server" show="true">
This example code will slowly drain away all rivers and seas.

``` lua
local level = 0

function drainSomeWater()
    level = level - 0.01
    setWaterLevel ( level )
end
setTimer ( drainSomeWater, 100, 15000 )
```

This example code adds a command *water* which can be used to change the current water level.

``` lua
addCommandHandler ( "water",
    function ( thePlayer, command, level )
        if level and tonumber ( level ) then -- if we have input something and if it is actually a number value
            setWaterLevel ( tonumber( level ) ) -- change the water level
            outputChatBox ( "Waterlevel is now: " .. level ) -- send a message to everyone to inform about the change
        end
    end
)
```

</section>
Issues
------

See Also
--------
