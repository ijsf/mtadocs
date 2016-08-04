This function will return the current heat haze effect settings.

**Note:** The server can only return the heat haze settings if it has actually been set by script.

Syntax
------

``` lua
int, int, int, int, int, int, int, int, bool getHeatHaze ( )
```

### Returns

Returns 9 values, which are the same used as arguments in [SetHeatHaze](/docs/setheathaze.md "wikilink"):

Example
-------

<section name="Client" class="client" show="true">
This example outputs current heat haze settings to the chat when player uses command 'get\_haze'.

``` lua
addCommandHandler( 'get_haze',
    function( )
        local tNew = { getHeatHaze ( ) }
        outputChatBox( 
            string.format( 
                'intensity = %s ;randomShift = %s ;speedMin = %s ;speedMax = %s ;scanSizeX = %s ;scanSizeY = %s ;renderSizeX = %s \
                ;renderSizeY = %s ;bShowInside = %s ;', unpack( tNew )
            )
        )       
    end
)
```

</section>
See Also
--------
