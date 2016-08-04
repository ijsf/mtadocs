This function checks in which way the cursor is currently moving.

Syntax
------

``` lua
string getCursorMoveOn( )
```

### Returns

Returns left,right,up or down.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getCursorMoveOn()
    if ( isCursorShowing() ) then
    left = "left"
    right = "right"
    up = "up"
    down = "down"
    zero = "nil"
    if getElementData(localPlayer,"movew") == right then
    return right
    elseif getElementData(localPlayer,"movew") == left then
    return left
    elseif getElementData(localPlayer,"movew") == up then
    return up
    elseif getElementData(localPlayer,"movew") == down then
    return down
    elseif getElementData(localPlayer,"movew") == zero then
    return false
    end
    end
end

function executeMoveOn(cursorX,cursorY)
    if ( isCursorShowing() ) then
    setElementData(localPlayer,"moveX",cursorX)
    setElementData(localPlayer,"moveY",cursorY)
         if cursorX > cX then
         setElementData(localPlayer,"movew",right)
         elseif cursorX < cX then
         setElementData(localPlayer,"movew",left)
         elseif cursorY > cY then
         setElementData(localPlayer,"movew",down)
         elseif cursorY < cY then
         setElementData(localPlayer,"movew",up)
         end
    end
end
addEventHandler("onClientCursorMove",root,executeMoveOn)

setTimer(
function()
    if ( isCursorShowing() ) then
    local curX = getElementData(localPlayer,"moveX")
    local curY = getElementData(localPlayer,"moveY")
         if cursorX == cX then
         setElementData(localPlayer,"movew",zero)
         elseif cursorY == cY then
         setElementData(localPlayer,"movew",zero)
         end
    end
end
,50,0)

function previousM()
   if ( isCursorShowing() ) then
    cX = getElementData(localPlayer,"moveX")
    cY = getElementData(localPlayer,"moveY")
   end
end
setTimer(previousM,50,0)
```

</section>
Example
-------

<section name="Client-side example" class="client" show="true">
This clientside example checks in which way cursor is currently moving.

``` lua
bindKey ("m", "down",
function()
showCursor( not isCursorShowing() )
end
)

addEventHandler("onClientCursorMove",root,
function()
    if ( isCursorShowing() ) then
    moveOn = getCursorMoveOn()
    outputChatBox("cursor is moving on : " .. moveOn, localPlayer)
    end
end
)
```

</section>
By **ronwolf1705**.

See Also
--------
