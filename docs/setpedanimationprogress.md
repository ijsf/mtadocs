Sets the current animation progress of a player or ped.

Syntax
------

``` lua
bool setPedAnimationProgress ( ped thePed [, string anim, float progress] )
```

### Required Arguments

-   **thePed:** the player or ped you want to change animation progress.

### Optional Arguments

-   **anim:** the animation name currently applied to ped, if not supplied, the animation will stop
-   **progress:** current animation progress you want to apply, value from 0.0 to 1.0, if not supplied will default to 0.0

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example creates a ped, apply animation to it, and “freeze” the animation at half of overall animation time.

``` lua
function animRender( ped1 )
        setPedAnimationProgress(ped1, "M_SMKSTND_LOOP", 0.5)
        setTimer ( animRender, 50, 1, ped1 )
end

function makePed()
    local ped1 = createPed(56, 1, 1, 4)
    setPedAnimation( ped1, "SMOKING", "M_SMKSTND_LOOP")
    setTimer ( animRender, 50, 1, ped1 )
end
addCommandHandler("makemyped", makePed)
```

</section>
Issues
------

See Also
--------

[ru:setPedAnimationProgress](/docs/ru:setpedanimationprogress.md "wikilink")
