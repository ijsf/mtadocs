This function gets the radius of an [element](/element.md "wikilink"). Normally, sphere or circle-shaped elements tend to return a more accurate and expected radius than others with another shapes.

Syntax
------

``` lua
float getElementRadius ( element theElement )
```

### Required Arguments

-   **theElement:** The element to get the radius of. It can be any entity type, such as:
    -   **[Players](/player.md "wikilink")**.
    -   **[Peds](/ped.md "wikilink")**.
    -   **[Vehicles](/vehicle.md "wikilink")**.
    -   **[Objects](/object.md "wikilink")**.

### Returns

Returns a *float* containing the radius if the element is valid, *false* otherwise.

Example
-------

This example shows how to get and output the radius of every player who types the */getmyradius* command (which will always be *1*).

``` lua
local function outputLocalPlayerRadius()
    outputChatBox("Your radius is " .. getElementRadius(localPlayer))
end
addCommandHandler("getmyradius", outputLocalPlayerRadius)
```

See Also
--------
