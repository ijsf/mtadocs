This function gets the wave form data for an audio stream which is a table of floats representing the current audio frame as a wave. This allows things like visualisations.

Syntax
------

``` lua
table getSoundWaveData ( element sound, int iSamples )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") [element](/docs/element.md "wikilink") that is created using [playSound](/docs/playsound.md "wikilink") or [playSound3D](/docs/playsound3d.md "wikilink"). Streams are also supported
-   **iSamples:** allowed samples are 256, 512, 1024, 2048, 4096, 8192 and 16384.

### Returns

Returns a [table](/docs/table.md "wikilink") of **iSamples**/2 floats representing the current audio frame waveform. Returns *false* if the sound is not playing yet or hasn't buffered in the case of streams.

Example
-------

This code creates vertical waveform of sound in center of screen from top to bottom. [1](http://imageshack.com/a/img547/9052/xbrp.png) Key **9** - start, key **0** - stop.

<section name="Client" class="client" show="true">
``` lua
local handl = nil
local sx,_ = guiGetScreenSize()
local colors = { tocolor(255,0,0),tocolor(0,255,0) }
 
function clientRenderFunc()
    if(handl) then
    dxDrawRectangle(sx/2,0,1,256,tocolor(255,255,255,127))
        local bt = getSoundWaveData(handl,512)
    if(not bt) then return end
    for i=1,127 do
        dxDrawLine(sx/2+64*bt[2*i-1],i*2-2,sx/2+64*bt[2*(i+1)-1],(i+1)*2-2,colors[2])
        dxDrawLine(sx/2+64*bt[2*i],i*2-1,sx/2+64*bt[2*(i+1)],(i+1)*2-1,colors[1])
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
        handl = playSound('btr.mp3')
        addEventHandler("onClientRender",root,clientRenderFunc)
    addEventHandler("onClientSoundStopped",root,clientSoundStopFunc)
    end
end
 
function musicStopFunc()
    if(handl) then
        removeEventHandler("onClientRender",root,clientRenderFunc)
    removeEventHandler("onClientSoundStopped",root,clientSoundStopFunc)
        stopSound(handl)
        handl = nil
    end
end
 
bindKey("9","down",musicStartFunc)
bindKey("0","down",musicStopFunc)
```

</section>
Changelog
---------

See Also
--------

[ar:getSoundWaveData](/docs/ar:getsoundwavedata.md "wikilink")
