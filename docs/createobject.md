Creates an object in the GTA world.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **modelid:** a whole integer specifying the GTASA object model ID.
-   **x:** a floating point number representing the X coordinate on the map.
-   **y:** a floating point number representing the Y coordinate on the map.
-   **z:** a floating point number representing the Z coordinate on the map.

### Optional Arguments

-   **rx:** a floating point number representing the rotation about the X axis in degrees.
-   **ry:** a floating point number representing the rotation about the Y axis in degrees.
-   **rz:** a floating point number representing the rotation about the Z axis in degrees.

### Returns

-   The [object](/docs/object.md "wikilink") element if creation was successful.
-   *false* otherwise.

Example
-------

<section name="Example1" class="server" show="true">
This example creates an object when the resource starts:

``` lua
function mapLoad ( name )
   -- create an object at a specified position with a specified rotation
   createObject ( 1337, 5540.6654, 1020.55122, 1240.545, 90, 0, 0 )
end
addEventHandler ( "onResourceStart", resourceRoot, mapLoad )
```

</section>
<section name="Example2" class="server" show="true">
This example creates an object near player who write createObject:

``` lua
-- this function is called whenever someone types 'createObject' in the console:
function consoleCreateObject ( thePlayer, commandName )
   if ( thePlayer ) then
      local x, y, z = getElementPosition ( thePlayer ) -- get the player's position
      -- create a Object next to the player:
      local theObject = createObject ( 980, x + 2, y + 2, z, 0, 0, 0 )
      if ( theObject ) then -- check if the Obeject was created successfully
         outputConsole ( "Object created successfully", thePlayer )
      else
         outputConsole ( "Failed to create Object", thePlayer )
      end
   end
end
addCommandHandler ( "createObject", consoleCreateObject )
```

</section>
See Also
--------

[de:createObject](/docs/de:createobject.md "wikilink")
