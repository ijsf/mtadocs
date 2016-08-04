Sets the current animation of a player or ped. Not specifying the type of animation will automatically cancel the current one.

Syntax
------

``` lua
bool setPedAnimation ( ped thePed [, string block=nil, string anim=nil, int time=-1, bool loop=true, bool updatePosition=true, bool interruptable=true, bool freezeLastFrame = true] )
```

### Required Arguments

-   **thePed:** the player or ped you want to apply an animation to.

### Optional Arguments

-   **block:** the [animation](/Animations.md "wikilink") block's name.
-   **anim:** the name of the [animation](/Animations.md "wikilink") within the block.
-   **time:** how long the animation will run for in milliseconds.
-   **loop:** indicates whether or not the animation will loop.
-   **updatePosition:** will change the actual coordinates of the ped according to the animation. Use this for e.g. walking animations.
-   **interruptable:** if set to 'false' other tasks wont be able to interupt the animation. Setting this to 'false' also gives this function more power to override other animations that are running. For example, squatting after a jump can be terminated.
-   **freezeLastFrame:** ... (From 1.1 onwards).

### Returns

Returns *true* if succesful, *false* otherwise.

Example1
--------

<section name="Server" class="server" show="true">
This example creates a ped, rotates him, and makes him walk:

``` lua
function makePed()
   ped1 = createPed(56, 1, 1, 4)
   setPedRotation(ped1, 315)
   setPedAnimation( ped1, "ped", "WOMAN_walknorm")
end
addCommandHandler("makemyped", makePed)
```

</section>
Example2
--------

This example makes the player dance when he uses command /dance and stop when he uses the same command:

<section name="Client" class="client" show="true">
``` lua

addEventHandler("onClientPreRender",root,
  function ()
    daBlock, daAnim = getPedAnimation(getLocalPlayer())
    setElementData(root,"blockz",daBlock)
    setElementData(root,"animz",daAnim)
  end )
```

</section>
<section name="Server" class="server" show="true">
``` lua
function dance (source)
    daBlockz = getElementData(root,"blockz")
    daAnimz = getElementData(root,"animz")
        if daBlockz == "dancing" and daAnimz == "dnce_m_b" then
            setPedAnimation(source,false)
        else
            setPedAnimation ( source, "DANCING", "dnce_m_b")
        end
    end
addCommandHandler("dance",dance)
```

</section>
See Also
--------

[ru:setPedAnimation](/ru:setPedAnimation.md "wikilink")
