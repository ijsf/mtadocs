This function is used to toggle the health target marker on top of all pedestrians.

Syntax
------

``` lua
bool setPedTargetingMarkerEnabled ( bool enabled )
```

### Required Arguments

-   **enabled:** A boolean denoting whether we want to enable (*true*) or disable (*false*) the markers.

### Returns

Returns *true* if the markers were enabled, *false* if weren't or if invalid arguments are passed.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function disableTargetMarkers()
    setPedTargetingMarkerEnabled(false) -- Disables target markers from being rendered after the resource is started
end
addEventHandler("onClientResourceStart", resourceRoot, disableTargetMarkers)
```

</section>
See Also
--------
