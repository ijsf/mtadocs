This function is used to reset the state of a player. It is intended to restore a player to his default state as if he had just joined the server, without any scripts affecting him.

Syntax
------

``` lua
bool resetMapInfo ( [player thePlayer = getRootElement()] )
```

### Optional Arguments

-   **thePlayer:** The specific player you wish to restore the state of. Not specifying this will result in all players map info being reset.

Returns
-------

Returns *true* if the map info was reset successfully, otherwise *false*.

Example
-------

This will reset all map info when the resource is stopped.

``` lua
addEventHandler("onResourceStop", getResourceRootElement(getThisResource()),
    -- Resource stop event
    function()
            resetMapInfo()
        end
)
```

See Also
--------
