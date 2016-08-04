<lowercasetitle></lowercasetitle>

This function Move it Gui right to center.

<div style="background: #FFCFCF; padding: 5px; font-weight:bold; border: 1px dotted #AAAAAA;padding:10px;margin:10px;">
<center>
<font color="#0066cc"  size="5">See also!</font>

<https://wiki.multitheftauto.com/wiki/GuiMoveTopToCenter> <https://wiki.multitheftauto.com/wiki/GuiMoveDownToCenter> <https://wiki.multitheftauto.com/wiki/GuiMoveLeftToCenter>

</center>
</div>
Syntax
------

``` lua
gui GuiMoveRightToCenter ( element gui)
```

Code
----

``` lua

TimeGuiSetRightC = { }

function guiMoveRightToCenter(gui)
if getElementData(gui,"HelhGui") == false then
    setElementData(gui,"HelhGui",true)
    local s1,s2=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (s1-w1)/2,(s2-w2)/2
    guiSetPosition(gui,-x,y,false) 

TimeGuiSetRightC[gui] = setTimer(guiMoveRightToCenter,50,0,gui)
end
    local a,b=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (a-w1)/2,(b-w2)/2
    local x1,y1 = guiGetPosition ( gui, false)
if (x1 >= x) then
    killTimer(TimeGuiSetRightC[gui])
    setElementData(gui,"HelhGui",false)
    else
    guiSetPosition(gui,x1+10,y,false)
end
end
```

Example
-------

<section name="Example" class="both" show="true">
``` lua

TimeGuiSetRightC = { }

function guiMoveRightToCenter(gui)
if getElementData(gui,"HelhGui") == false then
    setElementData(gui,"HelhGui",true)
    local s1,s2=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (s1-w1)/2,(s2-w2)/2
    guiSetPosition(gui,-x,y,false) 

TimeGuiSetRightC[gui] = setTimer(guiMoveRightToCenter,50,0,gui)
end
    local a,b=guiGetScreenSize()
    local w1,w2=guiGetSize(gui,false)
    local x,y = (a-w1)/2,(b-w2)/2
    local x1,y1 = guiGetPosition ( gui, false)
if (x1 >= x) then
    killTimer(TimeGuiSetRightC[gui])
    setElementData(gui,"HelhGui",false)
    else
    guiSetPosition(gui,x1+10,y,false)
end
end




addEventHandler( "onClientResourceStart",resourceRoot,
    function ( startedRes )
    myWindow = guiCreateWindow ( 0, 0, 0.3, 0.3, "Booo", true )
    myLabel = guiCreateLabel  ( 0.2,0.2,0.3, 0.3, "u love me?",true,myWindow)
        guiMoveRightToCenter(myWindow)
end
)
```

</section>
Author: Booo

See Also
--------
