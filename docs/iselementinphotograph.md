This function can be used with any weapon, but is more accurate when executed when the player shoots the weapon and the weapon is a camera.
\* **NOTE:** This is made to be used clientside!.

Syntax
------

``` lua
bool isElementInPhotograph( element theElement )
```

### Required Arguments

-   **theElement**: The element to be checked.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function isElementInPhotograph(ele)
    local nx, ny, nz = getPedWeaponMuzzlePosition(localPlayer)
    if (ele ~= localPlayer) and (isElementOnScreen(ele)) then -- Determine whether the element is even on the screen and not the client
        local px, py, pz = getElementPosition(ele)
        local _, _, _, _, hit = processLineOfSight(nx, ny, nz, px, py, pz) -- Check if there is a collision between the "camera viewpoint" and the element
        if (hit == ele) then -- If it collides with the element return true
            return true
        end
    end

    return false
end
```

</section>
Example
-------

``` lua
-- todo
```

Credits: qaisjp's getPlayersInPhotograph() function stripped down by DRLINE

See Also
--------
