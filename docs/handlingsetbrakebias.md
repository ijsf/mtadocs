Sets the brake bias of a handling element. This determines how the braking power is distributed over the wheels.

Syntax
------

``` lua
bool handlingSetBrakeBias ( handling theHandling, float bias )
```

### Required Arguments

-   **theHandling:** the handling of which you want to change the brake bias.
-   **bias:** the bias to set. This is a value between 0 and 1. A value of 0 will put all the braking power in the rear wheels, and the front wheels will not brake at all. A value of 1 has only the front wheels brake. With a bias of 0.5, front and back wheels have the same braking power.

### Returns

Returns *true* on success, *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
