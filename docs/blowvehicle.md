This function will blow up a vehicle. This will cause an explosion and will kill the driver and any passengers inside it.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool blowVehicle ( vehicle vehicleToBlow, [ bool explode=true ] )
```

### Required Arguments

-   **vehicleToBlow:** the vehicle that you wish to blow up.

### Optional Arguments

-   **explode:** if this argument is *true* then the vehicle will explode, otherwise it will just be blown up silently.

</section>
<section name="Client" class="client" show="true">
``` lua
bool blowVehicle ( vehicle vehicleToBlow )
```

### Required Arguments

-   **vehicleToBlow:** the vehicle that you wish to blow up.

</section>
### Returns

Returns *true* if the vehicle was blown up, *false* if invalid arguments were passed to the function.

Example
-------

<section name="Example 1: Server and client" class="both" show="true">
This example will blow up every vehicle in the game.

``` lua
vehicles = getElementsByType ( "vehicle" )
for vehicleKey, vehicleValue in ipairs(vehicles) do
    blowVehicle ( vehicleValue )
end
```

It is worth noting that the same could be achieved with the following:

``` lua
blowVehicle ( root ) -- root (getRootElement) is a built in MTA variable and therefore we do not have to define it.
```

</section>
<section name="Example 2: Server" class="server" show="true">
This example will blow a player's vehicle when he enters the car, like a carbomb.

``` lua
riggedVehicle = createVehicle(445, 0, 0, 5)
function blowVehicleEnter ( thePlayer, seat, jacked )
    --ENGINE START BOMB. 
    if seat == 0 then --check if the seat the player got into was id 0 - i.e. driver seat
        blowVehicle ( source ) --if it was, toast him
    end
end
addEventHandler ( "onVehicleEnter", riggedVehicle, blowVehicleEnter ) --trigger the function when a certain vehicle is entered
```

</section>
Client Class Example
--------------------

**Heads up!** Client classes only work on **MTA 1.4**, therefore we highly recommend you to visit [Client Scripting Classes](/docs/Client_Scripting_Classes.md "wikilink") first.

<section name="Example 1: Client" class="client" show="true">
This script will create an Infernus at the center (0, 0, 3) of San Andreas upon execution.

``` lua
addEventHandler( "onClientResourceStart", resourceRoot,
    function()
        infernus = Vehicle.create( 411, Vector3( 0, 0, 3 ) ); -- Create an Infernus and spawn it at the middle of SA.
        infernus:setColor( 0, 0, 0 ); -- Set its color to black.
    end)
    
addCommandHandler( "blowinfernus",
    function()
        if not infernus.blown then -- Check if the Infernus is blown up or not.
            infernus:blow();
        else -- Ouch, it's blown up, let's output an error to the client.
            outputChatBox( "The Infernus has already been blown up by you.", 255, 0, 0, false );
        end
    end)
```

</section>
See Also
--------
