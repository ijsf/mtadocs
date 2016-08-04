This function allows you to set the [dimension](/docs/dimension.md "wikilink") of any element. The dimension determines what/who the element is visible to.

Syntax
------

``` lua
bool setElementDimension ( element theElement, int dimension )
```

### Required Arguments

-   **theElement:** The element in which you'd like to set the dimension of.
-   **dimension:** An integer representing the dimension ID

### Returns

Returns *true* if **theElement** and **dimension** are valid, *false* otherwise. Also returns false if **theElement** is a player and it's not alive.

Example
-------

<section name="Server" class="server" show="true">
In this example the player's dimension is set to ID 1 when they enter a vehicle, and set back to dimension 0 when they exit the vehicle.

``` lua
function onPlayerEnterVehicle ( theVehicle, seat, jacked )
      if ( getElementDimension ( source ) == 0 ) then    -- if the player is in dimension 0
            setElementDimension ( source, 1 )            -- set his dimension to 1
            setElementDimension ( theVehicle, 1 )        -- set his vehicle's dimension to 1 as well
      end
end
addEventHandler ( "onPlayerVehicleEnter", root, onPlayerEnterVehicle )

function onPlayerExitVehicle ( theVehicle, seat, jacker )
      if ( getElementDimension ( source ) == 1 ) then    -- if the player is in dimension 1
            setElementDimension ( source, 0 )            -- set his dimension back to 0
            setElementDimension ( theVehicle, 0 )        -- set his vehicle's dimension back to 0 as well
      end
end
addEventHandler ( "onPlayerVehicleExit", root, onPlayerExitVehicle )
```

</section>
See Also
--------

[de:setElementDimension](/docs/de:setelementdimension.md "wikilink")
