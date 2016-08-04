This function allows you to set the camera's current goggle effect. This means you can activate nightvision or infrared effects by script

Syntax
------

``` lua
bool setCameraGoggleEffect ( string goggleEffect )
```

### Required Arguments

-   **goggleEffect**: the goggle effect you wish to set

### Returns

-   *true* if the effect was set correctly.
-   *false* otherwise.

Example
-------

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
