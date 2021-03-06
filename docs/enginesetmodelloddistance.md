This function sets a custom LOD distance for any object / model ID. This is the distance at which objects of that model ID are switched to their LOD model, or (if there is no LOD model) become invisible.

**Notes:** The actual draw distance used is modified by the draw distance slider in the settings 'Video' tab of the MTA client.

-   When the 'Video' tab draw distance slider is 0%, the engineSetModelLODDistance setting approximately matches the draw distance used.

  
*e.g. engineSetModelLODDistance(1337,100) will mean model 1337 will be visible up to a distance of **100** units.*

-   When the 'Video' tab draw distance slider is 100%, the engineSetModelLODDistance setting is approximately doubled before use.

  
*e.g. engineSetModelLODDistance(1337,100) will mean model 1337 will be visible up to a distance of **200** units.*

However, there is a general draw distance limit of 300 units. So engineSetModelLODDistance(1337,400) will mean model 1337 will be visible up to a distance of 300 units no matter what the 'Video' tab says.

Therefore, unless it's really important, engineSetModelLODDistance should not be set to anything greater than 170.
170 will still give the maximum draw distance (of 300 units) on clients that have a 'Video' tab draw distance setting of 100%, and it will help reduce lag for players who chose a lower draw distance in their settings.

Syntax
------

``` lua
bool engineSetModelLODDistance ( int model, float distance ) 
```

### Required Arguments

-   **model:** The model / object ID number you want to change the LOD distance of.
-   **distance:** New LOD distance value in San Andreas units.

### Returns

Returns *true* if the function executed succesfully, *false* otherwise.

Example
-------

``` lua
-- Cause massive lag by maxing out draw distance of all objects
for i, v in ipairs(getElementsByType("object")) do
    local model = getElementModel(v)
    engineSetModelLODDistance(model, 300)   -- Set maximum draw distance
end
```

See Also
--------
