This resource lets You create billboards. Billboard is a quad that always faces the camera. In this case billboard Elements are created using dxDrawMaterialLine3d MTA function. I have changed the behaviour of the material to act as cylindrical billboards do. There are many possibilities to use this resource. But that's all up to you.

Overview
--------

It is easy to use, gives a few options to manage billboards.

The resource itself adds exported clientside functions:

Exported functions
------------------

#### createBillboard

<section name="Client" class="client" show="true">
This function creates a shadered materialLine3d billboard.

``` lua
billboardElement exports.custom_billboards:createBillboard(float posX,posY,posZ,sizeX,sizeY,int colorR,colorG,colorB,colorA)
```

### Required Arguments

-   **float posX, posY, posZ:** Position in world space.
-   **float sizeX, sizeY:** Size of the billboard.
-   **int colorR,colorG,colorB,colorA:** RGBA color (0 - 255).

### Returns

The function returns billboardElement if set successfully, false otherwise.

</section>
#### destroyBillboard

<section name="Client" class="client" show="true">
This function destroys a shadered materialLine3d billboard element.

``` lua
bool exports.custom_billboards:destroyBillboard(element billboardElement)
```

### Required Arguments

-   **element billboardElement:** A previously declared billboard element.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBillboardMaterial

<section name="Client" class="client" show="true">
This function sets the billboard material (ex. texture).

``` lua
bool exports.custom_billboards:setBillboardMaterial(element billboardElement)
```

### Required Arguments

-   **element billboardElement:** A previously declared billboard element.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBillboardPosition

<section name="Client" class="client" show="true">
This function sets billboard position.

``` lua
bool exports.custom_billboards:setbillboardPosition(element billboardElement,float posX,posY,posZ)
```

### Required Arguments

-   **element billboardElement:** A previously declared billboard element.
-   **float posX, posY, posZ:** Position in world space.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBillboardSize

<section name="Client" class="client" show="true">
This function sets billboard size.

``` lua
bool exports.custom_billboards:setBillboardSize(element billboardElement,float size)
```

### Required Arguments

-   **element billboardElement:** A previously declared billboard element.
-   **float size:** Size of the billboard.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBillboardSizeXY

<section name="Client" class="client" show="true">
This function sets billboard width and height.

``` lua
bool exports.custom_billboards:setBillboardSizeXY(element billboardElement,float sizeX,sizeY)
```

### Required Arguments

-   **element billboardElement:** A previously declared billboard element.
-   **float sizeX,sizeY:** The width and height of the billboard.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBillboardDepthBias

<section name="Client" class="client" show="true">
On createBillboard the depthBias is set properly (0-1). You can however set other value depending on your needs. To see the results you'll need to set enableDepthBiasScale to true.

``` lua
bool exports.custom_billboards:setBillboardDepthBias(element billboardElement,float depthBiasValue)
```

### Required Arguments

-   **element billboardElement:** A previously declared billboard element.
-   **float depthBiasValue:** depthBias value.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBillboardColor

<section name="Client" class="client" show="true">
This function sets light color values.

``` lua
bool exports.custom_billboards:setbillboardColor(element billboardElement,float colorR,colorG,colorB,colorA)
```

### Required Arguments

-   **element billboardElement:** A previously declared billboard element.
-   **float colorR,colorG,colorB,colorA:** RGBA color (0 - 255).

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBillboardsDistFade

<section name="Client" class="client" show="true">
Set the Max distance of the billboard to sync and the distance on which the it starts to fade out.

``` lua
bool exports.custom_billboards:setBillboardsDistFade(int MaxEffectFade,int MinEffectFade)
```

### Required Arguments

-   **int MaxEffectFade:** Set the Max distance of the billboard to sync.(Must be greater than MinEffectFade).
-   **int MinEffectFade:** Set the distance on which the billboard starts to fade out.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### enableDepthBiasScale

<section name="Client" class="client" show="true">
Standard depthBias for GTASA coronas is about 1 unit, despite the corona scale. This function elables depthBias scaling.

``` lua
bool exports.custom_billboards:enableDepthBiasScale(bool isDepthScaleEnabled)
```

### Required Arguments

-   **bool isDepthScaleEnabled:** Enable/disable depthBias scaling.

### Returns

The function returns true if set successfully, false otherwise.

</section>
Examples
--------

``` lua
local tex = dxCreateTexture("hello.jpg")
function addStuff()
    for i=1,30 do
        for j=1,30 do
            exports.custom_billboards:createBillboard(tex,i * 7,j * 7,10,4,4,math.random()*255,math.random()*255,math.random()*255,1*255) 
        end 
    end
end

addEventHandler("onClientResourceStart", getResourceRootElement( getThisResource()), addStuff)
```

This creates 400 lovely billboards near position (0,0,0)

``` lua
local vehicle1 = nil
addEventHandler("onClientVehicleEnter", getRootElement(),
    function(thePlayer, seat)
        if thePlayer == getLocalPlayer() then
            vehicle1 = source
        end
    end
)

local tex = dxCreateTexture("hello.jpg")
local carLight = exports.custom_billboards:createBillboard(tex,0,0,0,4,4,math.random()*255,math.random()*255,math.random()*255,1*255)
addEventHandler("onClientPreRender", root, function()
    if vehicle1 then 
        xxx1,yyy1,zzz1 = getElementPosition(vehicle1)
        exports.custom_billboards:setBillboardPosition(carLight,xxx1,yyy1,zzz1)
    end
end
) 
```

This creates a billboard and attaches it to a vehicle that the player enters.

Of course when you want to use these functions in your resources you have to include the custom\_billboards resource in meta.

See Also
--------

[Resource download link](http://community.multitheftauto.com/index.php?p=resources&s=details&id=10156)

[Test resource](https://www.dropbox.com/s/vvsvua1kmrpjxaz/custom_billboards_test.zip?dl=0)
