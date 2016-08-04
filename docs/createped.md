Creates a Ped in the GTA world.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
 )
```

### Required Arguments

-   **modelid:** A whole integer specifying the [GTASA skin ID](/docs/character_skins.md "wikilink").
-   **x:** A floating point number representing the X coordinate on the map.
-   **y:** A floating point number representing the Y coordinate on the map.
-   **z:** A floating point number representing the Z coordinate on the map.

Optional Arguments
------------------

-   **rot:** A floating point number representing the rotation in degrees.
-   **synced:** A boolean value representing whether or not the ped will be synced. Disabling the sync might be useful for frozen or static peds to increase the server performance.

</section>
<section name="Client" class="client" show="true">
``` lua
 )
```

### Required Arguments

-   **modelid:** A whole integer specifying the [GTASA skin ID](/docs/character_skins.md "wikilink").
-   **x:** A floating point number representing the X coordinate on the map.
-   **y:** A floating point number representing the Y coordinate on the map.
-   **z:** A floating point number representing the Z coordinate on the map.

Optional Arguments
------------------

-   **rot:** A floating point number representing the rotation in degrees.

</section>
### Returns

Returns a ped element if it was successfully created.

Example
-------

<section name="Server" class="server" show="true">
This example creates an ped when the resource starts:

``` lua
function pedLoad ( name )
   createPed ( 120, 5540.6654, 1020.55122, 1240.545 )
end
addEventHandler ( "onResourceStart", getResourceRootElement(), pedLoad )
```

</section>
<section name="Client" class="client" show="true">
This example creates a ped, and makes it damage proof:

``` lua
thePed = createPed(120, 5540.6654, 1020.55122, 1240.545) -- Creates a ped
function cancelPedDamage()
    cancelEvent() -- Cancels the onClientPedDamage event
end
addEventHandler("onClientPedDamage", thePed, cancelPedDamage) -- When thePed is damaged, cancelPedDamage is called
```

</section>
Issues
------

See Also
--------

[pl:createPed](/docs/pl:createped.md "wikilink") [ru:createPed](/docs/ru:createped.md "wikilink")
