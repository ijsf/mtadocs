This function allows you to set the current rotation of the specified ped.

Syntax
------

``` lua
bool setPedRotation ( ped thePed, float rotation [, bool conformPedRotation = false ] )         
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") to set the rotation of
-   **rotation:** A [float](/float.md "wikilink") specifying the desired rotation in degrees.

### Optional Arguments

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example allows a player to type the command 'disco', which will result in the player being rotated to a random direction every 1 second, infinite times.

    function discoTime ( )
         -- Randomly choose a new player rotation and set it
         newRotation = math.random ( 0, 360 )
         setPedRotation ( getLocalPlayer(), newRotation )
    end

    function initiateDiscoMode ( commandName )
         -- Trigger a random change in player rotation every second
         setTimer ( discoTime, 1000, 0 )
    end
    addCommandHandler ( "disco", initiateDiscoMode )

</section>
Changelog
---------

See Also
--------

[ru:setPedRotation](/ru:setPedRotation.md "wikilink")
