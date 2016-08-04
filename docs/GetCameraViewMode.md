This function allows you to get the camera's view mode. This indicates at what distance the camera will follow the player.

-   **Note:** It currently only returns vehicle view modes

Syntax
------

``` lua
int getCameraViewMode (  )
```

### Returns

Returns an [int](/docs/int.md "wikilink") indicating the current camera view mode. Their meanings can be seen below.

Example
-------

This example tells the player their current camera view when they change it

``` lua
function onPlayerSpawn ( theSpawnpoint )
    currentCam("fire") -- start a repeating check
end
addEventHandler ( "onClientPlayerSpawn", root, onPlayerSpawn )

function currentCam(key)
   if (getControlState(key)) then
      outputChatBox("Your current cam view is: "..getCameraViewMode()..".")
   end
end
```

See Also
--------
