This function creates a [progress bar](/Element/GUI/Progress_bar.md "wikilink").

Syntax
------

``` lua
element guiCreateProgressBar ( float x, float y, float width, float height, bool relative, [element parent = nil] )
```

### Required Arguments

[frame|Example GUI progress bar.](/Image:Gui-progressbar.png.md "wikilink")

-   **x:** A float of the 2D x position of the progress bar on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the progress bar on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the progress bar. This is affected by the *relative* argument.
-   **height:** A float of the height of the progress bar. This is affected by the *relative* argument.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the progress bar is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns [element](/element.md "wikilink") of the progress bar if it was created succesfully, *false* otherwise.

Example
-------

This example creates a progress bar to player's screen on client resource start and destroys it when client resource stops.

<section name="Client-side script" class="client" show="true">
``` lua
function clientResourceStart( )
    progressBar = guiCreateProgressBar( 0.8, 0.8, 0.1, 0.1, true, nil )
end
addEventHandler( "onClientResourceStart", resourceRoot, clientResourceStart )

function clientResourceStop( )
    destroyElement( progressBar )
end
addEventHandler( "onClientResourceStop", resourceRoot, clientResourceStop )
```

</section>
See Also
--------
