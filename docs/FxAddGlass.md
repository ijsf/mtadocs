[thumb|200px|Glass](/docs/Image:Fxglass.png.md "wikilink") This function creates a glass particle effect.

Syntax
------

``` lua
bool fxAddGlass ( float posX, float posY, float posZ, [int colorR=255, int colorG=0, int colorB=0, int colorA=255, float scale=1.0, int count=1] )
```

### Required Arguments

-   **posX:** A float representing the **x** position of the glass
-   **posY:** A float representing the **y** position of the glass
-   **posZ:** A float representing the **z** position of the glass

### Optional Arguments

-   **colorR, colorG, colorB, colorA:** the color and alpha (transparency) of the glass effect.
-   **scale:** A float representing the size of the particle effect, where **1** is the standard size.
-   **count:** The density of the particle effect.

### Returns

Returns a true if the operation was successful, false otherwise.

Examples
--------

This example creates a glass particle effect at the position of the player who use /addGlass command.

``` lua
function addGlassParticle(cmd,r,g,b,a,scale,count)
   if r and g and b then 
      local x,y,z = getElementPosition(localPlayer)
      fxAddGlass(x+3,y,z,r,g,b,255,1.0,5)
   end 
end
addCommandHandler("addGlass",addGlassParticle)
```

See Also
--------
