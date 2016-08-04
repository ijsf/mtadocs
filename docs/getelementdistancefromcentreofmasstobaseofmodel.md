This function is used to retrieve the distance between a [element](/docs/element.md "wikilink")'s centre of mass to the base of the model. This can be used to calculate the position the [element](/docs/element.md "wikilink") has to be set to, to have it on ground level.

Syntax
------

``` lua
float getElementDistanceFromCentreOfMassToBaseOfModel ( element theElement )
```

### Required Parameters

**theElement:** The element you want to retrieve the value of.

### Returns

Returns a *float* with the distance, or *false* if the element is invalid.

Example
-------

This example outputs the value for the local player.

``` lua
local distance = getElementDistanceFromCentreOfMassToBaseOfModel(localPlayer)
outputChatBox(tostring(distance))
```

See Also
--------
