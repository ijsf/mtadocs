Syntax
------

``` lua
bool setNearClipDistance ( float distance )
```

### Required arguments

-   **distance:** the new near clip distance. It must be between **0.1** and **20** for the function to do any effect. Default value is **0.3**.

### Returns

This function returns *true* if the argument is valid. Returns *false* otherwise.

Example
-------

This example allows the camera to be nearer to ground level without viewing what is under it.

    setNearClipDistance(0.1) -- Start rendering things three times nearer than usual to archieve the effect described above

See also
--------
