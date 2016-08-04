This function returns the offsets of an element that has been attached to another element using [attachElements](/attachElements.md "wikilink").

Syntax
------

``` lua
float, float, float, float, float, float getElementAttachedOffsets ( element theElement )
```

### Required Arguments

-   **theElement:** The attached element.

### Returns

Returns 6 [floats](/float.md "wikilink"), of which the first 3 indicate the position offset (x, y, z), and the last 3 indicate the rotation offset (x, y, z), if successful. *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
**Example:** This example creates a car with a minigun

``` lua
-- Offsets
local x,y,z,rx,ry,rz= 0,-1.5,-0.1,0,0,-90

function createArmedBobcat(cmd)
    local lx, ly, lz = getElementPosition(localPlayer) -- get the position of the player
    lx = lx + 5 -- add 5 units to the x position
    
    veh = createVehicle( 422, lx, ly, lz) -- create a bobcat
    base = createObject( 2985, 2,2,2) -- create a minigun_base object
    setElementCollisionsEnabled ( base, false ) -- the minigun_base damages the car
    -- you could alternatively load an empty col file for the minigun object
    attachElements ( base, veh,  x,y,z,rx,ry,rz) -- attach the base to the bobcat
end

function rotateIt(cmd, addZ)
    if(addZ) then
        local x, y, z, rx, ry, rz = getElementAttachedOffsets (base) -- get the offsets
        rz = rz + addZ
        setElementAttachedOffsets (base, x, y, z, rx, ry, rz) -- update offsets
    end
end

addCommandHandler("bobcat", createArmedBobcat)
addCommandHandler("rotate", rotateIt)
```

</section>
See Also
--------
