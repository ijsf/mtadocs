This function is used to enable or disable occlusions. Occlusions are used by GTA to enhance performance by hiding objects that are (normally) obscured by certain large buildings. However when [removeWorldModel](/docs/removeWorldModel.md "wikilink") is used they may also have the undesired effect of making parts of the map disappear. Disabling occlusions will fix that.

Syntax
------

``` lua
bool setOcclusionsEnabled ( bool enabled )
```

### Required Arguments

-   **enabled:** A bool specifying if GTA occlusions should be enabled

### Returns

Returns *true* if the setting was set correctly, *false* if invalid arguments were passed.

Example
-------

This example shows occlusions being disabled after the whole map has been cleared:

``` lua
-- Remove all world models
for i=550,20000 do
    removeWorldModel(i,10000,0,0,0)
end
-- Turn off occlusions
setOcclusionsEnabled( false )
```

Requirements
------------

See Also
--------
