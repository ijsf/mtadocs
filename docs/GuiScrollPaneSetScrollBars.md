This function allows a scrollpane's scrollbars to be forced **on**, or returned to default.

Syntax
------

``` lua
bool guiScrollPaneSetScrollBars ( element scrollPane, bool horizontal, bool vertical )
```

### Required Arguments

-   **scrollPane:** the GUI scrollpane element you want to set the scrollbars of.
-   **horizontal:** A bool where true forces the horizontal scrollbar on, and false returns them to default.
-   **vertical:** A bool where true forces the vertical scrollbar on, and false returns them to default.

### Returns

Returns *true* if the call was successfully, *false* otherwise.

Example
-------

This example just checks to see if the scrollpane is created then sets the scrollbars. (TESTED!)

``` lua
scrollpane = guiCreateScrollPane(332,195,286,249,false)

if(scrollpane)then
    guiScrollPaneSetScrollBars(scrollpane,true,true)
end
```

See Also
--------
