Syntax
------

``` lua
int getCameraShakeLevel ( )
```

### Returns

Returns an integer representing the camera shake level, from 0 (no shaking effect) to 255 (maximum shaking effect). By default, the camera has no shaking effect.

Example
-------

This example checks for changes in the camera shake level of any player every frame and outputs different messages according to it.

``` lua
local lastDrunkLevel = getCameraShakeLevel()
local function warnPlayerAboutDrunkenness()
    local currentDrunkLevel = getCameraShakeLevel()
    if currentDrunkLevel ~= lastDrunkLevel and (currentDrunkLevel == 0 or currentDrunkLevel == 255) then
        outputChatBox(currentDrunkLevel == 255 and "You're completly drunk! You should stop drinking!" or "Now you are completely sober! You sohuld keep it like that.", currentDrunkLevel == 255 and 255 or 0, currentDrunkLevel == 0 and 255 or 0, 0)
    end
    lastDrunkLevel = currentDrunkLevel
end
addEventHandler("onClientRender", root, warnPlayerAboutDrunkenness)
```

See also
--------
