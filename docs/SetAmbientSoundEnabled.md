This function allows you to disable some background sound effects.

Syntax
------

``` lua
bool setAmbientSoundEnabled( string theType, bool enable )
```

### Required Arguments

-   **theType:** The type of ambient sound to toggle. Can be either “gunfire” or “general”.
-   **enable :** Set *false* to turn off, *true* to turn on

### Returns

Returns *true* if the ambient sound was set correctly, *false* if invalid values were passed.

Example
-------

This example turns off the ambient water and gunfire sounds:

``` lua
setAmbientSoundEnabled( "general", false )
setAmbientSoundEnabled( "gunfire", false )
```

See Also
--------
