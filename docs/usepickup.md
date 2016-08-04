This function is used to simulate the player using a pickup

Syntax
------

``` lua
bool usePickup ( pickup thePickup, player thePlayer )    
```

### Required Arguments

-   **thePickup**: The pickup element to be picked up/used.
-   **thePlayer**: The player to use the pickup.

Example
-------

<section name="Server" class="server" show="true">
This example gives a random player 100% armor by using a pickup.

``` lua
local pickup = createPickup(3,3,3,1,100) -- Create a pickup for 100% armor
usePickup(pickup,getRandomPlayer()) -- Make a random player use the pickup (shall recieve 100% armor)
```

</section>
See Also
--------
