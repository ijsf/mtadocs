This function is for creating and animating a dX Window.

-   **NOTE:** This is made to be used clientside!.

Syntax
------

``` lua
bool dxDrawAnimWindow ( string text, int height, int width, int color, string element font, string anim)
```

### Required Arguments

-   **text:** The text of the window
-   **height:** The height of the window
-   **width:** The width of the window
-   **color:** The color of the window
-   **font:** A element or string representing the font.
-   **anim:** The easing or animation type. See <https://wiki.multitheftauto.com/wiki/Easing>\] For more Types-

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function dxDrawAnimWindow(text,height,width,color,font,anim)
    local x,y = guiGetScreenSize()
 
    btwidth = width
    btheight = height/20
 
    local now = getTickCount()
    local elapsedTime = now - start
    local endTime = start + 1500
    local duration = endTime - start
    local progress = elapsedTime / duration
    local x1, y1, z1 = interpolateBetween ( 0, 0, 0, width, height, 255, progress, anim)
    local x2, y2, z2 = interpolateBetween ( 0, 0, 0, btwidth, btheight, btheight/11, progress, anim)
 
    posx = (x/2)-(x1/2)
    posy = (y/2)-(y1/2)
 
    dxDrawRectangle ( posx, posy-y2, x2, y2, color )
    dxDrawRectangle ( posx, posy, x1, y1, tocolor ( 0, 0, 0, 200 ) )
    dxDrawText ( text, 0, -(y1)-y2, x, y, tocolor ( 255, 255, 255, 255 ), z2,font,"center","center")   
 
 
end
```

</section>
Use
---

Always remeber to define the “start” value with getTickCount() and use onClientRender or onClientPreRender

<section name="Clientside example" class="client" show="true">
``` lua
function content()
     local color = tocolor ( 0, 0, 0, 200 )
     dxDrawAnimWindow ( "My Animated Window", 520, 600, color, "default-bold", "OutBounce")
end
bindKey ( "F2", "down", main )
function main()
     start = getTickCount()
     addEventHandler ( "onClientRender", getRootElement(), content )
end
```

</section>
Author: Bc\#

See Also
--------
