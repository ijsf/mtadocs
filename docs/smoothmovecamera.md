<lowercasetitle/>

This function allows you to create a cinematic-camera-flight, which moves from a specific position to a specific position.

Syntax
------

``` lua
bool smoothMoveCamera ( float x1, float y1, float z1, float x1t, float y1t, float z1t, float x2, float y2, float z2, float x2t, float y2t, float z2t, int time )
```

-   **x1, y1, z1**: The camera's start position.
-   **x1t, y1t, z1t**: The camera's start look at.
-   **x2, y2, z2**: The camera's end position.
-   **x2t, y2t, z2t**: The camera's end look at.
-   **time**: The speed of the camera's movement.

Code
----

<section name="Clientside Script" class="client" show="true">
``` lua
local sm = {}
sm.moov = 0
sm.object1,sm.object2 = nil,nil
 
local function removeCamHandler()
    if(sm.moov == 1)then
        sm.moov = 0
    end
end
 
local function camRender()
    if (sm.moov == 1) then
        local x1,y1,z1 = getElementPosition(sm.object1)
        local x2,y2,z2 = getElementPosition(sm.object2)
        setCameraMatrix(x1,y1,z1,x2,y2,z2)
    end
end
addEventHandler("onClientPreRender",root,camRender)
 
function smoothMoveCamera(x1,y1,z1,x1t,y1t,z1t,x2,y2,z2,x2t,y2t,z2t,time)
    if(sm.moov == 1)then return false end
    sm.object1 = createObject(1337,x1,y1,z1)
    sm.object2 = createObject(1337,x1t,y1t,z1t)
    setElementAlpha(sm.object1,0)
    setElementAlpha(sm.object2,0)
    setObjectScale(sm.object1,0.01)
    setObjectScale(sm.object2,0.01)
    moveObject(sm.object1,time,x2,y2,z2,0,0,0,"InOutQuad")
    moveObject(sm.object2,time,x2t,y2t,z2t,0,0,0,"InOutQuad")
    sm.moov = 1
    setTimer(removeCamHandler,time,1)
    setTimer(destroyElement,time,1,sm.object1)
    setTimer(destroyElement,time,1,sm.object2)
    return true
end
```

</section>
Author: Noneatme(Me) \[Fixed by ADCX, does not give errors now\]

See Also
--------
