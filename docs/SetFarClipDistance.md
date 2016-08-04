This function is used to set the distance of render. Areas beyond the specified distance will not be rendered.

Syntax
------

``` lua
bool setFarClipDistance ( float distance )
```

### Required Arguments

-   **distance:** A float specifying the distance of render.

### Returns

Returns *true* if the distance was set correctly, *false* if invalid arguments were passed.

Example
-------

<section name="Server" class="server" show="true">
This example adjusts the visibility range of the game world.

``` lua
addEventHandler( "onResourceStart", resourceRoot,
    function( )
        setFarClipDistance( 3000 ) -- We adjust visibility range to 3000 metres
    end
)
```

</section>
<section name="Client" class="client" show="false">
This example adjusts the visibility range of the game world.

``` lua
addEventHandler( "onClientResourceStart", resourceRoot,
    function( )
        setFarClipDistance( 3000 ) -- We adjust visibility range to 3000 metres
    end
)
```

</section>
See Also
--------
