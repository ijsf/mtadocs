This function returns whether any system windows that take focus are active. This includes:

-   Chatbox input
-   Console window
-   Main menu
-   Transferbox

To get the status of the debug view, see [isDebugViewActive](/docs/isdebugviewactive.md "wikilink").

Syntax
------

``` lua
bool isMTAWindowActive ()
```

### Returns

Returns *true* if the focus is on the MTA window, *false* if it isn't.

Example
-------

This piece of script will kill a player if he has any of the above system windows open

``` lua
function dontAllowAnyOpenWindow ()
    if isMTAWindowActive () then
         setElementHealth ( getLocalPlayer(), 0.0 )
    end  
end
setTimer ( dontAllowAnyOpenWindow, 50, 0 )
```

See Also
--------

[ru:isMTAWindowActive](/docs/ru-ismtawindowactive.md "wikilink")
