Retrieve the rotation of elements.

Syntax
------

``` lua
float float float getElementRotation ( element theElement [, string rotOrder = "default" ] )       
```

### Required Arguments

-   **theElement:** The element whose rotation will be retrieved

### Optional Arguments

-   **rotOrder:** A string representing the rotation order desired when returning the [euler angles](http://en.wikipedia.org/wiki/Euler_angles). If omitted, default value is *“default”*. Allowed values are:
    -   *“default”:* default MTA behavior prior to 1.1, where rotation order depends on element type
    -   *“ZXY”:* rotation about the Z axis (*up*), then about the resulting X axis (*right*) and finally about the resulting Y axis (*front*). This is the default rotation order for [objects](/docs/object.md "wikilink")
    -   *“ZYX”:* rotation about the Z axis (*up*), then about the resulting Y axis (*front*), and finally about the resulting X axis (*right*). This is the default rotation order for [vehicles](/docs/vehicle.md "wikilink")

The default rotation order for peds/players is Z-Y-X (clientside) and -Z-Y-X (serverside) but those rotation orders (set using *“default”* on peds) can not be used manually on other element types since they only exist due to historical and backward compatibility reasons. Specifying a rotation order other than *“default”* allows the same angles to later be uniformly used on several elements without having to consider their type.

### Returns

-   *rx, ry, rz*: 3 *float*s representing the Euler rotation angles on the axis X, Y and Z (with the rotation order depending on the *rotOrder* argument) if *element* exists and is a valid element, *false* if it's invalid.

Example
-------

If a player points at a player element with a gun, its rotation will appear in the chat box.

<section name="Client" class="client" show="true">
``` lua
function onPlayerTargeted ( targetElem )
    if ( isElement(targetElem) and getElementType (targetElem) == "player" ) then
        local x,y,z = getElementRotation ( targetElem )
        outputChatBox ( "Target player rotation: " .. x .. " " .. y .. " " .. z )
    end
end
addEventHandler ( "onClientPlayerTarget", root, onPlayerTargeted )
```

</section>
See Also
--------
