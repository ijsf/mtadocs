This function gets the left/right level from a [sound](/sound.md "wikilink") [element](/element.md "wikilink").

Syntax
------

``` lua
int, int getSoundLevelData ( element theSound )
```

### Required Arguments

-   **theSound:** the [sound](/sound.md "wikilink") [element](/element.md "wikilink") which level data you want to return.

### Returns

Returns a 2 values with Left, Right level data from sound (range is \[0,32768\]), *false* otherwise.

Example
-------

This code creates vertical lines of right and left level in center of screen from top to bottom. [1](http://imageshack.com/a/img716/8689/4ud1.png) Key **9** - start, key **0** - stop.

``` lua
local handl = nil
local sx,_ = guiGetScreenSize()
local colors = { tocolor(255,0,0),tocolor(0,255,0) }
 
function clientRenderFunc()
    if(handl) then
    local ls,rs = getSoundLevelData(handl)
    if(ls ~= false) then
            dxDrawRectangle(sx/2-10,0,10,128*(ls/32768),colors[1])
            dxDrawRectangle(sx/2+10,0,10,128*(rs/32768),colors[2])
    end
    end
end

function clientSoundStopFunc(_)
    if(source == handl) then
    removeEventHandler("onClientRender",root,clientRenderFunc)
    removeEventHandler("onClientSoundStopped",root,clientSoundStopFunc)
    handl = nil
    end
end
 
function musicStartFunc()
    if(not handl) then
        handl = playSound('nya.mp3')
        addEventHandler("onClientRender",root,clientRenderFunc)
    addEventHandler("onClientSoundStopped",root,clientSoundStopFunc)
    end
end
 
function musicStopFunc()
    if(handl) then
        stopSound(handl)
        handl = nil
        removeEventHandler("onClientRender",root,clientRenderFunc)
    removeEventHandler("onClientSoundStopped",root,clientSoundStopFunc)
    end
end
 
bindKey("9","down",musicStartFunc)
bindKey("0","down",musicStopFunc)
```

Requirements
------------

Changelog
---------

See Also
--------

[ar:getSoundLevelData](/ar:getSoundLevelData.md "wikilink")
