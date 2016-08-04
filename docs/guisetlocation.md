<pageclass class="#228B22" subcaption="Useful Function"></pageclass> <lowercasetitle/>

This function will change gui Location to Horizontal and Vertical location.

Syntax
------

``` lua
string guiSetLocation ( element Gui, string Horizontal, string Vertical )
```

### Required Arguments

-   **Gui**: The guiElement to be changed.
-   **Horizontal**: “left”, “center”, “right”.
-   **Vertical**: “up”, “center”, “down”.

Code
----

<section name="Function source" class="client" show="true">
``` lua
x3NAD = { 
    xLocation = {
        ["right"] = { 1 };
        ["left"] = { 10 };
        ["center"] = { 2 };
    };
    yLocation = {
        ["up"] = { 10 };
        ["down"] = { 1 };
        ["center"] = { 2 };     
    };
};
 
guiSetLocation = function ( gui, Horizontal, Vertical )
    local screenW, screenH = guiGetScreenSize ( )
    local windowW, windowH = guiGetSize ( gui, false )
    if Horizontal and Vertical then
        local x, y = tonumber ( x3NAD.xLocation[Horizontal][1] ) or 2, tonumber ( x3NAD.yLocation[Vertical][1] ) or 2
        local x, y = ( screenW -windowW ) /x, ( screenH -windowH ) /y
        guiSetPosition ( gui, x, y, false )
    end
end;
```

</section>
Example
-------

<section name="Client-side example" class="client" show="true">
``` lua
window = guiCreateWindow ( 100, 100, 400, 400, "Test", false );
guiSetLocation ( window, "left", "down" );
```

</section>
-   This Function Has Created By **3NAD**.

See Also
--------

[Category:Useful Functions](/docs/Category:Useful_Functions.md "wikilink")
