This function center the window in any resolution.
\* **NOTE:** This is made to be used clientside!.

Syntax
------

``` lua
bool centerWindow ( element TheElement )
```

### Required Arguments

-   **theElement**: The element you want to center it.

### Returns

Returns *true* if the window has been successfully centered, *false* otherwise.

Example
-------

<section name="Clientside script" class="client" show="true">
``` lua
function centerWindow (center_window)
    local screenW, screenH = guiGetScreenSize()
    local windowW, windowH = guiGetSize(center_window, false)
    local x, y = (screenW - windowW) /2,(screenH - windowH) /2
    return guiSetPosition(center_window, x, y, false)
end
```

</section>
Example
-------

This example center the window.

``` lua
addEventHandler( "onClientResourceStart", resourceRoot, function()
  myWindow = guiCreateWindow( 350, 100, 200, 250, "Window Title", false )
end )

addCommandHandler( "center", function()
  if myWindow then
    centerWindow( myWindow )
  end
end )
```

Author: laserlaser

See Also
--------
