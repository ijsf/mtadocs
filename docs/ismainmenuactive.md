This function returns whether the user is in the mainmenu or not.

Syntax
------

``` lua
bool isMainMenuActive ()
```

### Returns

Returns *true* if the mainmenu is visible, *false* if not.

Example
-------

This example check if the player is afk.

``` lua
function isLocalPlayerActive ()
   if isMainMenuActive() then
      setElementData(getLocalPlayer(),"status","afk")
   else
      setElementData(getLocalPlayer(),"status","playing")
   end
end
```

See Also
--------
