Syntax
------

``` lua
int getMoonSize ()
```

### Returns

Returns a integer being the moon size that is currently set, depending on which side it is used.

Example
-------

<section name="Server" class="server" show="true">
This example will tell the moon size to everyone when the resource is started.

``` lua
function handleResourceStart( )
    outputChatBox( string.format( "Server's moon size is set to %d", getMoonSize() ) )
end
addEventHandler( "onResourceStart", resourceRoot, handleResourceStart )
```

</section>
Requirements
------------

See Also
--------
