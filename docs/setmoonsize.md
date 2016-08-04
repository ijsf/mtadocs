Syntax
------

``` lua
bool setMoonSize ( int size )
```

### Required Arguments

-   **size:** The size, can be 0 or any positive value. Default is **3**.

### Returns

Returns true if the moon size was set correctly, false otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example change moon size to looks more realistic for everyone when the resource is started.

``` lua
function handleResourceStart( )
    setMoonSize( 0 )
end
addEventHandler( "onResourceStart",  resourceRoot, handleResourceStart )
```

</section>
Requirements
------------

See Also
--------
