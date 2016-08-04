Enables or disables a special world property (cheat).

Syntax
------

``` lua
bool setWorldSpecialPropertyEnabled ( string propname, bool enable )
```

### Required Arguments

-   **propname:** the name of the property to set. Possible values are:
    -   **hovercars** - equivalent of the JBGVNB cheat, and allows cars to drive on water.
    -   **aircars** - equivalent of the RIPAZHA cheat, and allows cars to fly.
    -   **extrabunny** - equivalent of the CJPHONEHOME or JHJOECW cheat, and allows you to bunny hop on bicycles much higher.
    -   **extrajump** - equivalent of the KANGAROO cheat, and allows you to jump on foot much higher.
-   **enable:** whether or not to enable the property.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

Function which allow cars to fly.

<section name="Client" class="client" show="true">
``` lua
addEventHandler( "onClientResourceStart", resourceRoot,
function()
setWorldSpecialPropertyEnabled("aircars", true)
end
)
```

</section>
**Example 2:** Allow cars to drive on water.

<section name="Client" class="client" show="true">
``` lua
addEventHandler( "onClientResourceStart", resourceRoot,
function()
setWorldSpecialPropertyEnabled("hovercars", true)
end
)
```

</section>
See Also
--------
