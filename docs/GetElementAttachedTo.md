This function determines the element that the specified element is attached to.

Syntax
------

``` lua
element getElementAttachedTo ( element theElement )  
```

### Required Arguments

-   **theElement:** The element you require the information for.

### Returns

Returns the element that the chosen element is attached to, or *false* if the element isn't attached to another element.

Example
-------

<section name="Server" class="server" show="true">
This example defines a console command that outputs the type of the element that the player is attached to.

``` lua
function getAttached ( thePlayer )
    local attached = getElementAttachedTo ( thePlayer )
    if ( attached ) then
        outputConsole ( getPlayerName(thePlayer) .. " is attached to a " .. getElementType(attached) )
    else
        outputConsole ( getPlayerName(thePlayer) .. " is not attached to an element" )
    end
end
addCommandHandler ( "getattached", getAttached )
```

</section>
See Also
--------
