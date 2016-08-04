This function gets the LOD distance for any object / model ID.

Syntax
------

``` lua
float engineGetModelLODDistance ( int model ) 
```

### Required Arguments

-   **model:** The model / object ID number you want to get the LOD distance of.

### Returns

Returns a float representing the LOD distance of the model, or *false* if the model argument is incorrect.

Example
-------

This example calculates the actual LOD distance by taking into account the Video tab 'Draw distance' setting

``` lua
local LODDistance = engineGetModelLODDistance( 1337 )
local actualLODDistance = math.min( 300, LODDistance * ( dxGetStatus().SettingDrawDistance / 100 + 1 ) )
```

Requirements
------------

See Also
--------
