This function brings a dxGUI element on top of others.

Syntax
------

``` lua
dxSetAlwaysOnTop( element dxElement, bool postGUI )
```

### Required Arguments

-   **dxElement:** the dxGUI element that you want to move to the front.
-   **postGUI:** the dxGUI element state. If this is true than the element will be on top

Example
-------

**Example 1:** This brings on top the window.

``` lua
window = exports.dxGUI_v1:dxCreateWindow(0,0,250,300,"Hello!",white,"default-bold","Sath Metro [Green]")
exports.dxGUI_v1:dxSetAlwaysOnTop(window, true)
```
