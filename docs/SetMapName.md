This function is used to set a map name that will be visible in the server browser. In practice you should generally rely on the mapmanager to do this for you.

Syntax
------

``` lua
bool setMapName ( string mapName )
```

### Required Arguments

-   **mapName:** The name you wish the server browser to show.

### Returns

Returns *true* if map name was set successfully, *false* otherwise.

Example
-------

This example sets the map name to *My amazing map!* when the resource is started.

``` lua
addEventHandler("onResourceStart", getResourceRootElement(), function() setMapName("My amazing map!") end)
```

See Also
--------
