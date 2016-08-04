This is a normal map resource for MTA. It enables normal mapping effect for peds. Also adds sun and moon light to make gtasa lighting a bit more interesting. It is compatible with the peds created to work with normalmap plugin for gtasa.

Overview
--------

You'll have to extract normals from the txd file and apply them with the applyNormalToPedTexture function.

This test resource should present a better explanation. [Download here](http://www.solidfiles.com/d/be237103ee/) Choose (!SKIN ID 7!) after starting.

The resource itself adds exported clientside functions:

Exported functions
------------------

#### applyNormalToPedTexture

<section name="Client" class="client" show="true">
This function applies the normal mapping effect to ped textures.

``` lua
bool exports.shaderPedNormal:applyNormalToPedTexture( table filepath strings )
```

### Required Arguments

-   **filepath strings:** The table of filepaths to apply. Those should be paths for the normals extracted from the txd archive.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### removeNormalFromPedTexture

<section name="Client" class="client" show="true">
This function removes the normal mapping effect from ped textures.

``` lua
bool exports.shaderPedNormal:removeNormalFromPedTexture( table filepath strings )
```

### Required Arguments

-   **filepath strings:** The table of previously applied normals to be disabled.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### applySpecularToGTAPeds

<section name="Client" class="client" show="true">
This function applies a custom specular lighting effect to ped by ID.

``` lua
bool exports.shaderPedNormal:applySpecularToGTAPeds(table ped model id table,bool sobel)
```

### Optional Arguments

-   **ped model id table:** The ped model id table If left blank the effect is applied to all standard ped textures.
-   **sobel:** The second argument generates normals based on original textures if set true. Sobel filter works only when your graphics card supports shader model 3.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### removeSpecularFromGTAPeds

<section name="Client" class="client" show="true">
This function removes custom specular lighting effect from ped by ID.

``` lua
bool exports.shaderPedNormal:removeSpecularFromGTAPeds(table ped model ids)
```

### Optional Arguments

-   **ped model ids:** the ped model id table If left blank the effect is removed from all ped textures.

### Returns

The function returns true if set successfully, false otherwise.

</section>
Examples
--------

``` lua
local resourceName = ":"..getResourceName(getThisResource()).."/" 
exports.shaderPedNormal:applyNormalToPedTexture({resourceName.."normals/face_nrm1.0.png",resourceName.."normals/skin_nrm1.0.png"})
```

This applies normal map effect to textures “face” and “skin”. Notice that the nrm textures should be placed in the resource the function is being called from.

``` lua
exports.shaderPedNormal:applySpecularToGTAPeds({0,7,121},false)
```

This applies the specular effect to peds by id 0,7,121

``` lua
exports.shaderPedNormal:removeSpecularFromGTAPeds()
```

removes the specular effect from all the peds.

Of course when you want to use theese functions in your resources you have to include the ShaderPedNormal resource in meta.

See Also
--------

[Resource page on community.mtasa](https://community.multitheftauto.com/index.php?p=resources&s=details&id=7665)
