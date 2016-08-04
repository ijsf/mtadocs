Syntax
------

``` lua
bool, bool getCameraClip() 
```

### Returns

-   **objects:** if you want the camera to clip on objects.
-   **vehicles:** if you want the camera to clip on vehicles.

Example
-------

This function checks the clip status.

``` lua
function checkClipStatus()
  local obj, veh = Camera.getClip()
  outputChatBox ("Your camera can" .. (veh and "" or "not") .. "see the vehicle interior at the moment!",255,0,0,false)
  outputChatBox ("Your camera can" .. (obj and "" or "not") .. "collide with objects at the moment!",255,0,0,false)
end
addEventHandler("clipstatus",checkClipStatus)
```

See Also
--------
