This function will enable or disable clouds. This is useful for race maps which are placed high up as clouds can cause low FPS.

Syntax
------

``` lua
bool setCloudsEnabled ( bool enabled )
```

### Required Arguments

-   **enabled:** A [boolean](/boolean.md "wikilink") value determining if clouds should be shown. Use *true* to show clouds and *false* to hide them.

### Returns

Returns *true* if the cloud state was changed succesfully, *false* if an invalid argument was specified.

Example
-------

<section name="Server" class="server" show="true">
This example Disables clouds for all players

``` lua
function disableClouds ()
    setCloudsEnabled ( false )    -- Hide the clouds for all players when the resource starts
end
addEventHandler ( "onResourceStart", getResourceRootElement(), disableClouds )
```

</section>
See Also
--------

[ru:setCloudsEnabled](/ru:setCloudsEnabled.md "wikilink")
