This function can be used to set a ped on fire or extinguish a fire on it.

Syntax
------

``` lua
bool setPedOnFire ( ped thePed, bool isOnFire )
```

### Required Arguments

-   **thePed:** The ped that we want to set/unset
-   **isOnFire:** *true* to set the ped on fire, *false* to extinguish any fire on him

### Returns

Returns *true* if successful, *false* otherwise

Example
-------

This script will set player on fire when they fall into water.

<section name="Client" class="client" show="true">
``` lua
addEventHandler("onClientResourceStart", resourceRoot,
    function ()
        setTimer(   function()
                        if isElementInWater(getLocalPlayer()) then
                            setPedOnFire ( getLocalPlayer(), true )
                        end
                    end, 1000, 0)
    end
    )    
```

</section>
See Also
--------

[ru:setPedOnFire](/docs/ru:setPedOnFire.md "wikilink")
