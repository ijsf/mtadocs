Sets the model of a given element. This allows you to change the model of a player (or ped), a vehicle or an object.

Syntax
------

``` lua
bool setElementModel ( element theElement, int model )
```

### Required Arguments

-   **theElement:** the element you want to change.
-   **model:** the model ID to set.
    -   For players/peds: A GTASA player model (skin) ID. See [Character Skins](/Character_Skins.md "wikilink").
    -   For vehicles: The [vehicle ID](/Vehicle_IDs.md "wikilink") of the vehicle being changed.
    -   For objects/projectiles/weapons: An [int](/int.md "wikilink") specifying the model id.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section class="server" name="Example 1 (Server)" show="true">
``` lua
addCommandHandler ( "changeveh",
    function ( thePlayer, command, newModel )
        local theVehicle = getPedOccupiedVehicle ( thePlayer ) -- get the vehicle the player is in
        newModel = tonumber ( newModel )                          -- try to convert the string argument to a number
        if theVehicle and newModel then                           -- make sure the player is in a vehicle and specified a number
            setElementModel ( theVehicle, newModel )
        end
    end
)
```

After the above code is executed, a player can get in any vehicle and execute e.g. the command "/changeveh 520" to change it into a hydra.

</section>
<section class="server" name="Example 2 (Server)" show="true">
This will continually change an object model every 2.5 seconds at the location -1084.52, -1634.81, 76.36 (Truth's farm).

``` lua
myobject = createObject ( 5822, -1084.52, -1634.81, 76.36 )
-- We create an initial object element. I choose object model 5822 to begin with.

function objectRandomization ()  
    local randomobjectnumber = math.random(1, 18000)
    -- Choose a random number between 1 and 18000 as a whole integer and assign it to
    -- the variable 'randomobjectnumber'
    setElementModel ( myobject, randomobjectnumber )
    -- Change our object appearance by applying a new model ID
end

setTimer ( objectRandomization, 2500, 0 )
-- Every 2.5 seconds, the function 'objectRandomization' is called by this timer.
-- Each time the function runs, it changes the object model by applying a new whole-
-- integer random object ID. This timer is called an infinite amount of times since  
-- its repeat value is set to 0.
```

</section>
See Also
--------
