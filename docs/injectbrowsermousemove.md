Syntax
------

``` lua
bool injectBrowserMouseMove ( browser webBrowser, int posX, int posY )
```

### Required arguments

-   **webBrowser:** The browser which will retrieve the mouse movement
-   **posX:** Absolute X screen coordinate
-   **posY:** Absolute Y screen coordinate

### Returns

Returns *true* if the movement was injected successfully, *false* otherwise.

Example
-------

``` lua
function onCursorMove ( relativeX , relativeY , absoluteX , absoluteY ) 
    injectBrowserMouseMove ( browser , absoluteX , absoluteY ) 
end 
addEventHandler ( "onClientCursorMove" , root , onCursorMove )
```

See Also
--------

Todo

See also
--------
