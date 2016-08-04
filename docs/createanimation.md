<lowercasetitle/>

This function allows you to use interpolateBetween without render event and easily used.

Syntax
------

``` lua
)
```

### Required arguments

-   **from**: the start value.
-   **to**: the end value.
-   **easing**: the [easing function](/docs/Easing.md "wikilink") to use for the animation or can be used the easing number, e.g. “Linear” = 1, “InQuad” = 2, “OutQuad” = 3, ...
-   **duration**: the duration of animation.
-   **onChange**: the function to call when the animation value is changed.

### Optional arguments

-   **onEnd**: the function to call when the animation End.

### Return

Returns true or false if invalid arguments were passed.

Code
----

<section name="Code" class="client" show="true">
``` lua
local anims = { }
local builtins={ "Linear", "InQuad", "OutQuad", "InOutQuad", "OutInQuad", "InElastic", "OutElastic", "InOutElastic", "OutInElastic", "InBack", "OutBack", "InOutBack", "OutInBack", "InBounce", "OutBounce", "InOutBounce", "OutInBounce", "SineCurve", "CosineCurve" }
function table.find(t, v)
    for k,a in ipairs(t) do
        if a == v then return true end
    end
    return false
end
function createAnimation(f, t, easing, duration, onChange, onEnd)
    assert(type(f) == "number", "Bad argument @ 'createAnimation' [expected number at argument 1, got "..type(f).."]")
    assert(type(t) == "number", "Bad argument @ 'createAnimation' [expected number at argument 2, got "..type(t).."]")
    assert(type(easing) == "string" or (type(easing) == "number" and (easing >= 1 or easing <= #builtins)), "Bad argument @ 'createAnimation' [Invalid easing at argument 3]")
    assert(type(duration) == "number", "Bad argument @ 'createAnimation' [expected function at argument 4, got "..type(duration).."]")
    assert(type(onChange) == "function", "Bad argument @ 'createAnimation' [expected function at argument 5, got "..type(onChange).."]")
    table.insert(anims, {from = f, to = t, easing = table.find(builtins, easing) and easing or builtins[easing], duration = duration, start = getTickCount( ), onChange = onChange, onEnd = onEnd})
    return true
end
addEventHandler("onClientRender", root, function( )
    local now = getTickCount( )
    for k,v in ipairs(anims) do
        if now >= v.start+v.duration then
            table.remove(anims, k)
            if type(v.onEnd) == "function" then
                v.onEnd( )
            end
        end
        v.onChange(interpolateBetween(v.from, 0, 0, v.to, 0, 0, (now - v.start) / v.duration, v.easing))
    end
end)
```

</section>
Example
-------

<section name="Example" class="client" show="true">
This example open/close with slide up/down effect.

``` lua
--Slide Animation
local sx, sy = guiGetScreenSize( )
local window = guiCreateWindow((sx-300)/2, (sy-400)/2, 300, 400, "Test", false)
guiSetVisible(window, false)
bindKey("f2", "down", function( )
    if anim then return end
    local v = guiGetVisible(window)
    if not v then guiSetVisible(window, true) end
    anim = true
    createAnimation(v and 400 or 0, v and 0 or 400, 2, 1250, function(height)
        if v and height == 0 then 
            guiSetVisible(window, false)
            anim = false
        elseif not v and height == 400 then
            anim = false
        end
        local w, h = guiGetSize(window, false)
        guiSetSize(window, w, height, false)
    end)
end
```

</section>
Other : Mr.Tn6eL

See Also
--------
