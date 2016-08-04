This function retrieves the local screen size according to the resolution they are using.

Syntax
------

``` lua
float float guiGetScreenSize()
```

### Returns

This returns two floats representing the player's screen resolution, *width* and *height*.

Example
-------

This example checks whether a player is using a low resolution, and warns them that GUI may appear incorrect.

``` lua
--setup a function when the resource starts
function checkResolutionOnStart ()
    local x,y = guiGetScreenSize() --get their screen size
    if ( x <= 640 ) and ( y <= 480 ) then --if their resolution is lower or equal to 640x480
        --warn them about GUI problems.
        outputChatBox ( "WARNING: You are running on a low resolution.  Some GUI may be placed or appear incorrectly." )
    end
end
--attach the function to the event handler
addEventHandler ( "onClientResourceStart", resourceRoot, checkResolutionOnStart )
```

Using guiGetScreenSize to fit GUI & DX drawing in all resolutions
-----------------------------------------------------------------

To get the precise coordinates of a GUI element or DX drawings, you need to decide which edges of the screen you want to have them positioned against, then you just need to find the difference between your screen size and your position values.

For example, there is a DX text. It fits on 1024x768 resolution.

``` lua
function DXtext ()
dxDrawText(tostring "Hello World!",684.0,731.0,732.0,766.0,tocolor(0,255,255,175),1.0,"bankgothic","left","top",false,false,false)
end

addEventHandler ( "onClientRender", getRootElement(), DXtext )
```

Now if you want it to fit on all resolutions. Then follow these steps:

1. Add *width* and *height* variables to get GUI's screen size, here we use sWidth and sHeight.

``` lua
local sWidth,sHeight = guiGetScreenSize() -- The variables
dxDrawText( "Hello World!",684.0,731.0,732.0,766.0,tocolor(0,255,255,175),1.0,"bankgothic","left","top",false,false,false)
```

2. Divide each of the DX text's position values by the screen size manually (remembering the resolution is 1024x768):

-   **Left** position value is 684, 684/1024 = 0.668
-   **Top** position value is 731, 731/768 = 0.952
-   **Right** position values is 732, 732/1024 = 0.715
-   **Bottom** position value is 766, 766/768 = 0.997

You may want to use a calculator to help you count.

3. Now with the answer above remove all of the position values and replace it with the width or height variable multiplied by the answer. Which would be:

``` lua
local sWidth,sHeight = guiGetScreenSize() -- The variables
dxDrawText("Hello World!",sWidth*0.668, sHeight*0.952, sWidth*0.715, sHeight*0.997,tocolor(0,255,255,175),1.0,"bankgothic","left","top",false,false,false)
```

So the final results will be a DX text which will fit on all resolutions which will be:

``` lua
function DXtext ()
local sWidth,sHeight = guiGetScreenSize() -- The variables
dxDrawText("Hello World!",sWidth*0.668, sHeight*0.952, sWidth*0.715, sHeight*0.997,tocolor(0,255,255,175),1.0,"bankgothic","left","top",false,false,false)
end

addEventHandler ( "onClientRender", getRootElement(), DXtext )
```

See Also
--------
