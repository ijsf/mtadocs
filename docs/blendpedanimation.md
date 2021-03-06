Sets the current animation of a player or ped. Not specifying the type of animation will automatically cancel the current one.

<section name="Client" class="client" show="true">
``` lua
bool blendPedAnimation ( ped thePed [, string block, string name, float speed=1.0, float blendSpeed=1.0, float startTime=0.0, bool loop=true, bool updatePosition=true, bool interruptable=false, function callbackFunction=nil, var arguments, ... ] )
```

### Required Arguments

-   **thePed:** the player or ped you want to apply an animation to.

### Optional Arguments

-   **block:** the [animation](/docs/animations.md "wikilink") block's name.
-   **anim:** the name of the [animation](/docs/animations.md "wikilink") within the block.
-   **speed:** the speed at which the animation is played.
-   **blendSpeed:** the speed at which the previous and current animation are blended.
-   **startTime:** how far into the animation (in seconds) you want to skip
-   **loop:** indicates whether or not the animation will loop.
-   **updatePosition:** will change the actual coordinates of the ped according to the animation. Use this for e.g. walking animations.
-   **interruptable:** If set to 'false', the animation will not be interrupted by other tasks (eg: falling)
-   **callbackFunction:** A function that is called when the animation is finished
-   **arguments:** Any arguments you want to pass to the callbackFunction, eg: animation name

</section>
### Returns

Returns *true* if succesful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example creates a ped, rotates them, and makes them walk:

``` lua
function makePed()
   ped1 = createPed(56, 1, 1, 4)
   setPedRotation(ped1, 315)
   blendPedAnimation(ped1, "ped", "WOMAN_walknorm")
end
addEventHandler("onClientResourceStart", getResourceRootElement(), makePed)
```

</section>
Issues
------

See Also
--------
