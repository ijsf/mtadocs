This function returns an element from the specified ID. If more than one element with the same ID exists, only the first one in the order it appears in the XML tree will be returned by this function.

Syntax
------

``` lua
element getElementByID ( string id [, int index = 0 ] )  
```

### Required Arguments

-   **id:** The ID of the element as it appears in the XML file or as set by [setElementID](/docs/setElementID.md "wikilink").

### Optional Arguments

-   **index:** If there are two or more elements of the same ID it will return the element with the specified index starting at 0.

### Returns

Returns the [element](/docs/element.md "wikilink") with the given ID, or *false* if no such element exists.

Example
-------

Assuming we have this in the .map file:

``` xml
<vehicle id="vipVehicle" posX="10" posY="10" posZ="4" model="602" />
```

Then this example would retrieve the element and output the vehicle name.

``` lua
function showVipVehicle()
    local vipVehicle = getElementByID("vipVehicle")
    outputChatBox("Vip Vehicle is a: "..getVehicleName(vipVehicle))
end
addCommandHandler("vipVehicle",showVipVehicle)
```

See Also
--------
