Used for custom Lua based interpolation, returns the easing value (animation time to use in your custom interpolation) given a progress and an [easing function](/Easing.md "wikilink"). In most cases, either [moveObject](/moveObject.md "wikilink") or [interpolateBetween](/interpolateBetween.md "wikilink") can do the job. getEasingValue is only provided in case you want to do your own custom interpolation based on easing.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **fProgress:** float between 0 and 1 indicating the interpolation progress (0 at the beginning of the interpolation, 1 at the end).
-   **strEasingType:** the [easing function](/Easing.md "wikilink") to use for the interpolation

### Optional Arguments

-   **fEasingPeriod:** the period of the [easing function](/Easing.md "wikilink") (only some easing functions use this parameter)
-   **fEasingAmplitude:** the amplitude of the [easing function](/Easing.md "wikilink") (only some easing functions use this parameter)
-   **fEasingOvershoot:** the overshoot of the [easing function](/Easing.md "wikilink") (only some easing functions use this parameter)

### Returns

Returns ''fAnimationTime '' the animation time given by the easing function (can be &lt; 0 or &gt; 1 since some [easing functions](/Easing.md "wikilink") have overshoot or bounce/spring effects, *false* otherwise (error in parameters).

Example
-------

The examples below are only clientside ones, even though the functions can be used on both sides. Indeed it makes more sense to use them with onClientRender/onClientPreRender but the freedom is given to use it in any other context.

<section name="Client" class="client" show="true">
This clientside example uses getEasingValue to make a custom camera fade. The command to test it is "/fade". The fading out is done with “InQuad” to have a slow fading which then accelerates and “OutQuad” is used for fading in to have a smooth end of the fading. In this example [interpolateBetween](/interpolateBetween.md "wikilink") could have been used directly to interpolate the alpha between 0 and 255 and then 255 and 0 but is example is just to illustrate the use of getEasingValue by itself.

``` lua
local g_Fade = nil
addCommandHandler("fade", 
function ()
    if g_Fade then return end
    g_Fade = {}
    g_Fade.startTime = getTickCount()
    g_Fade.endTime = g_Fade.startTime + 2000
    g_Fade.easingFunction = "InQuad" --Slow at first and accelerating
    addEventHandler("onClientRender", getRootElement(), fadeCameraOut)
end)

function fadeCameraOut()
    local now = getTickCount()
    local elapsedTime = now - g_Fade.startTime
    local duration = g_Fade.endTime - g_Fade.startTime
    local progress = elapsedTime / duration
    
    local fAnimationTime = getEasingValue(progress, g_Fade.easingFunction)
    
    local alpha = fAnimationTime*255
    local width, height = guiGetScreenSize()
    dxDrawRectangle(0, 0, width, height, tocolor(0, 0, 0, alpha), true)
    
    if now > g_Fade.endTime then
        removeEventHandler("onClientRender", getRootElement(), fadeCameraOut)
        g_Fade.startTime = getTickCount()
        g_Fade.endTime = g_Fade.startTime + 2000
        g_Fade.easingFunction = "OutQuad" --Fast at first then decelerating
        addEventHandler("onClientRender", getRootElement(), fadeCameraIn)
    end
end

function fadeCameraIn()
    local now = getTickCount()
    local elapsedTime = now - g_Fade.startTime
    local duration = g_Fade.endTime - g_Fade.startTime
    local progress = elapsedTime / duration
    
    local fAnimationTime = getEasingValue(progress, g_Fade.easingFunction)
    
    local alpha = (1-fAnimationTime)*255
    local width, height = guiGetScreenSize()
    dxDrawRectangle(0, 0, width, height, tocolor(0, 0, 0, alpha), true)
        
    if now > g_Fade.endTime then
        removeEventHandler("onClientRender", getRootElement(), fadeCameraIn)
        g_Fade = nil
    end
end
```

</section>
See Also
--------
