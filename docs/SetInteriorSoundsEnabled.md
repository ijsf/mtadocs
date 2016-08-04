This function disables or enables the ambient sounds played by GTA in most interiors, like restaurants, casinos, clubs, houses, etc.

Syntax
------

``` lua
bool setInteriorSoundsEnabled ( bool enabled )
```

-   **enabled:** set to *true* to enable the interior ambient sounds, *false* to disable them. By default they're enabled.

Returns
-------

If a boolean was passed to the function, it always succeeds and returns *true*.

Example
-------

<section name="Client" class="client" show="true">
This example disables the dancing club ambient music, without disabling other interiors' ambient sounds.

``` lua
function disableClubMusic()
    if getElementInterior(localPlayer) == 17 and getDistanceBetweenPoints3D(493.39, -22.72, 1000.68, getElementPosition(localPlayer)) < 50 and getInteriorSoundsEnabled() then
        setInteriorSoundsEnabled(false)
    elseif not getInteriorSoundsEnabled() then
        setInteriorSoundsEnabled(true)
    end
end
addEventHandler("onClientPreRender", root, disableClubMusic)
```

</section>
See also
--------
