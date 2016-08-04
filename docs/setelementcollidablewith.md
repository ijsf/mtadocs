This function can be used to set an element to collide with another element. An element with collisions disabled does not interact physically with the other element.
**Note:** You can only use this function with the element types listed below.

-   [Player](/docs/Player.md "wikilink")
-   [Ped](/docs/Ped.md "wikilink")
-   [Vehicle](/docs/Vehicle.md "wikilink")
-   [Object](/docs/Object.md "wikilink")

Syntax
------

``` lua
bool setElementCollidableWith ( element theElement, element withElement, bool enabled ) 
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") which colliding you want to change
-   **withElement:** The other [element](/docs/element.md "wikilink") you wish the first entity to collide with
-   **enabled:** A boolean to indicate whether elements should be able to collide with eachother (*true*) or not (*false*)

### Returns

Returns *true* if the collisions were set succesfully, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua

function ghostmode_on()
    local v = getPedOccupiedVehicle(localPlayer) -- Get her's Vehicle ID
    for index,vehicle in ipairs(getElementsByType("vehicle")) do --LOOP through all Vehicles
        setElementCollidableWith(vehicle, v, false) -- Set the Collison off with the Other vehicles.
    end
    outputChatBox("You are now a Ghost :P",thePlayer)
end
addCommandHandler("ghostmode", ghostmode_on) -- Add the /ghostmode Command.
```

</section>
See Also
--------
