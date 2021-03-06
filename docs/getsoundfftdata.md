This function gets the fast fourier transform data for an audio stream which is a table of floats representing the current audio frame. This allows things like visualisations.

a fast fourier transform generates a table of all the frequencies of the current audio frame which starts at the bass end of the spectrum to mids to highs in that order

Should you have any problems there is an example resource located on the resource svn here: [Visualiser](https://code.google.com/p/mtasa-resources/source/browse/#svn%2Ftrunk%2F%5Bgameplay%5D%2FVisualiser)

just type “startmusic mystreamurl” in your console and it will play on the cinema billboard near A51 If the element is a player, this function will use the players voice.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **sound:** a sound element that is created using [playSound](/docs/playsound.md "wikilink") or [playSound3D](/docs/playsound3d.md "wikilink"). Streams are also supported
-   **iSamples:** allowed samples are 256, 512, 1024, 2048, 4096, 8192 and 16384.

### Optional Arguments

-   **iBands:** post processing option allows you to split the samples into the desired amount of bands or bars so if you only need 5 bars this saves a lot of cpu power compared to trying to do it in Lua.

### Returns

Returns a table of **iSamples**/2 (or **iBands**-1 if **iBands** is used) floats representing the current audio frame. Returns false if the sound is not playing yet or hasn't buffered in the case of streams.

Example
-------

This code creates vertical spectrum analyzer with thin lines in center of screen from top to bottom. [1](http://imageshack.com/a/img543/79/i4oz.png) Key **9** - start, key **0** - stop.

<section name="Client" class="client" show="true">
``` lua
local handl = nil
local sx,_ = guiGetScreenSize()
local colors = { tocolor(255,0,0),tocolor(0,255,0) }
 
function clientRenderFunc()
    if(handl) then
    dxDrawRectangle(sx/2,0,1,256,tocolor(255,255,255,127))
        local bt = getSoundFFTData(handl,2048,257)
    if(not bt) then return end
        for i=1,256 do
            bt[i] = math.sqrt(bt[i])*256 --scale it (sqrt to make low values more visible)
            dxDrawRectangle(sx/2-bt[i]/2,i-1,bt[i],1)
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

</section>
Changelog
---------

See Also
--------

[ES:getSoundFFTData](/docs/es-getsoundfftdata.md "wikilink") [AR:getSoundFFTData](/docs/ar-getsoundfftdata.md "wikilink")
