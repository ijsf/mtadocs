This function changes the sky color to a two-color gradient.

Syntax
------

``` lua
bool setSkyGradient ( [ int topRed = 0, int topGreen = 0, int topBlue = 0, int bottomRed = 0, int bottomGreen = 0, int bottomBlue = 0 ] )
```

### Optional Arguments

-   **topRed:** The *red* value of the upper part of the sky, from 0 to 255.
-   **topGreen:** The *green* value of the upper part of the sky, from 0 to 255.
-   **topBlue:** The *blue* value of the upper part of the sky, from 0 to 255.
-   **bottomRed:** The *red* value of the lower part of the sky, from 0 to 255.
-   **bottomGreen:** The *green* value of the lower part of the sky, from 0 to 255.
-   **bottomBlue:** The *blue* value of the lower part of the sky, from 0 to 255.

### Returns

Returns *true* if sky color was set correctly, *false* if invalid values were passed.

Example
-------

This example sets the sky to a hot pink gradient.

<section name="Client" class="client" show="true">
``` lua
function ClientStarted ()
setSkyGradient( 200, 0, 100, 150, 0, 70 )
end 
addEventHandler( "onClientResourceStart", getResourceRootElement(getThisResource()), ClientStarted )
```

</section>
This example will set a blue **realistic sky**.

<section name="Client" class="client" show="true">
``` lua
function ClientStarted ()
setSkyGradient( 60, 100, 196, 136, 170, 212 )
end 
addEventHandler( "onClientResourceStart", getResourceRootElement(getThisResource()), ClientStarted )
```

</section>
See Also
--------

[ru:setSkyGradient](/docs/ru-setskygradient.md "wikilink")
