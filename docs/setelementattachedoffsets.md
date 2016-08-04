This function updates the offsets of an element that has been attached to another element using [attachElements](/docs/attachelements.md "wikilink").

Syntax
------

``` lua
bool setElementAttachedOffsets ( element theElement, [ float xPosOffset, float yPosOffset, float zPosOffset, float xRotOffset, float yRotOffset, float zRotOffset ])
```

### Required Arguments

-   **theElement:** The attached element.

### Optional Arguments

-   **xPosOffset:** The x offset, if you want the elements to be a certain distance from one another (default 0).
-   **yPosOffset:** The y offset (default 0).
-   **zPosOffset:** The z offset (default 0).
-   **xRotOffset:** The x rotation offset (default 0).
-   **yRotOffset:** The y rotation offset (default 0).
-   **zRotOffset:** The z rotation offset (default 0).

### Returns

Returns *true* if the attaching process was successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
**Example:** This example creates a car with a minigun

``` lua
-- Offsets
local x,y,z,rx,ry,rz= 0,-1.5,-0.1,0,0,-90

function createArmedBobcat(cmd)
    local lx,ly,lz = getElementPosition(root) -- get the position of the player
    lx = lx + 5 -- add 5 units to the x position
    
    veh = createVehicle( 422, lx, ly, lz) -- create a bobcat
    base = createObject( 2985, 2,2,2) -- create a minigun_base object
    setElementCollisionsEnabled ( base, false ) -- the minigun_base damages the car
    -- you could alternatively load an empty col file for the minigun object
    attachElements ( base, veh,  x,y,z,rx,ry,rz) -- attach the base to the bobcat
end

function rotateIt(cmd, addZ)
    if(addZ) then
        rz=rz+addZ
        setElementAttachedOffsets (base,x,y,z,rx,ry,rz) --update offsets
    end
end

addCommandHandler("bobcat", createArmedBobcat)
addCommandHandler("rotate", rotateIt)
```

</section>
See Also
--------
