<lowercasetitle></lowercasetitle>

This function Move it Gui top to center.

Syntax
------

``` lua
gui GuiMoveTopToCenter ( element gui)
```

Code
----

``` lua

TimeGuiSetTopC = { }

function guiMoveTopToCenter(gui)
if getElementData(gui,"HelhGui") == false then
    setElementData(gui,"HelhGui",true)
    local s1,s2=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (s1-w1)/2,(s2-w2)/2
    guiSetPosition(gui,x,-w2,false) 

TimeGuiSetTopC[gui] = setTimer(guiMoveTopToCenter,50,0,gui)
end
    local a,b=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (a-w1)/2,(b-w2)/2
    local x1,y1 = guiGetPosition ( gui, false)
if (y1 >= y) then
    killTimer(TimeGuiSetTopC[gui])
    setElementData(gui,"HelhGui",false)
    else
    guiSetPosition(gui,x1,(y1+10),false)
end
end
```

Example
-------

<section name="Example" class="both" show="true">
``` lua




TimeGuiSetTopC = { }

function guiMoveTopToCenter(gui)
if getElementData(gui,"HelhGui") == false then
    setElementData(gui,"HelhGui",true)
    local s1,s2=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (s1-w1)/2,(s2-w2)/2
    guiSetPosition(gui,x,-w2,false) 

TimeGuiSetTopC[gui] = setTimer(guiMoveTopToCenter,50,0,gui)
end
    local a,b=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (a-w1)/2,(b-w2)/2
    local x1,y1 = guiGetPosition ( gui, false)
if (y1 >= y) then
    killTimer(TimeGuiSetTopC[gui])
    setElementData(gui,"HelhGui",false)
    else
    guiSetPosition(gui,x1,(y1+10),false)
end
end








addEventHandler( "onClientResourceStart",resourceRoot,
    function ( startedRes )
    myWindow = guiCreateWindow ( 0, 0, 0.3, 0.3, "Booo", true )
    myLabel = guiCreateLabel  ( 0.2,0.2,0.3, 0.3, "u love me?",true,myWindow)
        guiMoveTopToCenter(myWindow)
end
)
```

</section>
Author: Booo

See Also
--------
