This checks if an element is visible to a player. This does not check if the player can literally see the element, just that they are aware that it exists. Some so-called [per-player elements](/per-player_elements.md "wikilink") are able to be visible only to some players, as such this checks if this is the case for a particular element/player combination.

Syntax
------

``` lua
bool isElementVisibleTo ( element theElement, element visibleTo )          
```

### Required Arguments

-   **theElement:** The element you want to check the visibility of
-   **visibleTo:** The player you want to check against

### Returns

Returns *true* if element is visible to the specified player, *false* if not or an invalid argument was passed to the function.

Example
-------

This checks if the player is visible to them selves.

``` lua
addEventHandler("onPlayerSpawn",root,function()
     if not isElementVisibleTo(source,source) then --if the player is not visible to them selves
          setElementVisibleTo(source,source,true) --then make them visible to them selves.
     end
end)
```

See Also
--------
