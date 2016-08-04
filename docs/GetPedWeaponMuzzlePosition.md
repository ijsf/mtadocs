Returns the world position of the muzzle of the weapon that a ped is currently carrying. The weapon muzzle is the end of the gun barrel where the bullets/rockets/... come out.

The position may not be accurate if the ped is off screen.

Syntax
------

``` lua
float, float, float getPedWeaponMuzzlePosition ( ped thePed )
```

### Required Arguments

-   **thePed:** the ped whose weapon muzzle position to retrieve.

### Returns

If successful, returns the x/y/z coordinates of the weapon muzzle. Returns *false* otherwise.

<section name="Client" class="client" show="true">
This Example draws a red 3D-Line when a Player shoots,between the Players WeaponMuzzlePosition and the Point where the Bullet hits.\[Tested\]

``` lua
    
function OnPlayerFire(w,a,aC,hX,hY,hZ,hE)-- the function to which onClientPlayerFire is attached, contains the Paramteres for the the Bullet hit Position
 local sx,sy,sz = getPedWeaponMuzzlePosition(source)-- get the WeaponMuzzlePosition of the Player who shot
 Position = {sx,sy,sz,hX,hY,hZ} -- save it in a table so we can use it later in 'onClientRender'function
 removeEventHandler("onClientRender",root,onRender)-- remove onClientRender-Event from function onRender  to not have multiple add for same function
 addEventHandler("onClientRender",root,onRender) -- add the onClientRender-Event to the function onRender
end -- end of function onPlayerFire
addEventHandler("onClientPlayerWeaponFire",root,OnPlayerFire)

function onRender() -- function to which onClientRender-Event will be attached.
 if Position then -- check if there are Positions available
  local startX,startY,startZ,endX,endY,endZ = unpack(Position)-- unpack the Position table
  dxDrawLine3D( startX,startY,startZ,endX,endY,endZ,tocolor(200,0,0,255),3) -- draws the 3D line between start-Position and end-Position
 end -- end of if
end -- end of onRender
```

</section>
See Also
--------
