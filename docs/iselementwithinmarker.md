This function is used to determine if an [element](/docs/element.md "wikilink") is within a [marker](/docs/marker.md "wikilink").

Syntax
------

``` lua
bool isElementWithinMarker ( element theElement, marker theMarker )
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") you're checking.
-   **theMarker:** The [marker](/docs/marker.md "wikilink") you're checking.

### Returns

Returns *true* if the element is within the marker, *false* otherwise

Example
-------

``` lua
dutymarker = createMarker(126.56, 254.98, 78.9, 'cylinder', 2.0, 255, 0, 0, 150)

function duty(thePlayer, matchingDimension)
 if isElementWithinMarker(thePlayer, dutymarker) then
    giveWeapon(thePlayer, 22, 100, 1)  
 else
    outputChatBox("You are not at the right place!", thePlayer, 255, 0, 0)
 end
end
addCommandHandler("duty", duty)
```

See Also
--------

[ru:isElementWithinMarker](/docs/ru-iselementwithinmarker.md "wikilink")
