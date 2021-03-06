Sets the suspension bias of a handling element. This determines the suspension force distribution over the front and back wheels.

Syntax
------

``` lua
bool handlingSetSuspensionFrontRearBias ( handling theHandling, float bias )
```

### Required Arguments

-   **theHandling:** the handling of which you want to change the suspension bias.
-   **bias:** A value between 0 and 1. At 0, the back wheels have all the suspension and the front wheels have none. At 1, the front wheels have suspension and the back wheels have none. With a value of 0.5, all wheels have the same suspension power.

### Returns

Returns *true* on success, *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
