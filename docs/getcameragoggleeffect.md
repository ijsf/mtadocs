This function returns what goggle effect is currently affecting the camera.

Syntax
------

``` lua
string getCameraGoggleEffect (  )
```

### Returns

-   [String](/docs/String.md "wikilink") indicating the current camera goggle effect. Their meanings can be seen below.

Example
-------

This example adds a command to enable or disable the nightvision effect.

``` lua
function nightvision()
    if (getCameraGoggleEffect() == "normal") then
        setCameraGoggleEffect("nightvision")
    elseif (getCameraGoggleEffect() == "nightvision") then
        setCameraGoggleEffect("normal")
    end
end

addCommandHandler("nightvision", nightvision)
```

See Also
--------
