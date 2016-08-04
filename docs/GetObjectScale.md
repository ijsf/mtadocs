This function returns the visible size of an object.

Syntax
------

``` lua
float getObjectScale ( object theObject )
```

### Required Arguments

-   **theObject**: the [object](/docs/object.md "wikilink") you wish to return the scale of.

### Returns

-   A [float](/docs/float.md "wikilink") indicating the scale of the object, if successful.
-   *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example adds a command *get\_scale* which create object and prints out a scale of the object.

``` lua
addCommandHandler( 'get_scale',
    function( )
        local uObject = createObject( 1337, getElementPosition( localPlayer ) )
        outputChatBox( string.format( 'Object scale is %s !', getObjectScale( uObject ) ) )
    end
)
```

</section>
See Also
--------
