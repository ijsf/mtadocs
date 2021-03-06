This resource lets You create dynamic lights in MTA. It gives you a list of exported functions that You can use to create per pixel pointlights and spotlights. It should be considered a preview of what [MTA:Eir](https://wiki.multitheftauto.com/wiki/MTA:Eir) will offer. The future solution should be more FPS friendly. Yet i see that resource as an example of what the future holds.

Overview
--------

It is easy to use, gives a few options to create per pixel lights in gtasa.

The resource itself adds exported clientside functions:

Exported functions
------------------

#### createPointLight

<section name="Client" class="client" show="true">
This function creates a pixel shader pointlight.

``` lua
)
```

### Required Arguments

-   **float posX, posY, posZ:** Light position in world.
-   **float colorR,colorG,colorB,colorA:** RGBA color emitted by the light (0 - 1 instead of 0-255).
-   **float attenuation:** Value specifying how the light intensity changes over distance.

### Optional Arguments

-   **bool normalShadow:** Determine if the light source should be obscured when lighting a surface on opposite angles.

### Returns

The function returns lightElement if set successfully, false otherwise.

</section>
#### createSpotLight

<section name="Client" class="client" show="true">
This function creates a pixel shader spotlight.

``` lua
)
```

### Required Arguments

-   **float posX, posY, posZ:** Light position in world space.
-   **float colorR,colorG,colorB,colorA:** RGBA color emitted by the light (0 - 1 instead of 0-255).
-   **float dirX,dirY,dirZ:** Direction that the light is pointing in world space. It's a vector as default.
-   **bool isEuler:** Is the angle set as an “ZXY” euler andgle or a vector.
-   **float falloff:** Decrease in illumination between a spotlight's inner cone (the angle specified by Theta) and the outer edge of the outer cone (the angle specified by Phi).
-   **float theta: (radians)** Angle, in radians, of a spotlight's inner cone - that is, the fully illuminated spotlight cone. This value must be in the range from 0 through the value specified by Phi.
-   **float phi: (radians)** Angle, in radians, defining the outer edge of the spotlight's outer cone. Points outside this cone are not lit by the spotlight. This value must be between 0 and pi.
-   **float attenuation:** Value specifying how the light intensity changes over distance.

### Optional Arguments

-   **bool normalShadow:** Determine if the light source should be obscured when lighting a surface on opposite angles.

### Returns

The function returns lightElement if set successfully, false otherwise.

</section>
#### destroyLight

<section name="Client" class="client" show="true">
This function destroys a light element.

``` lua
bool exports.dynamic_lighting:destroyLight(element lightElement)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightDirection

<section name="Client" class="client" show="true">
This function setd light direction values for both a pointlight and a spotlight.

``` lua
)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **float dirX,dirY,dirZ:** Direction that the light is pointing in world space. It's a vector as default.

### Optional Arguments

-   **bool isEuler:**Is the angle set as an “ZXY” euler andgle or a vector.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightPosition

<section name="Client" class="client" show="true">
This function sets light position values for both a pointlight and a spotlight.

``` lua
bool exports.dynamic_lighting:setLightPosition(element lightElement,float posX,posY,posZ)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **float posX, posY, posZ:** Light position in world space.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightColor

<section name="Client" class="client" show="true">
This function sets light color values for both a pointlight and a spotlight.

``` lua
bool exports.dynamic_lighting:setLightColor(element lightElement,float colorR,colorG,colorB,colorA)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **float colorR,colorG,colorB,colorA:** RGBA color emitted by the light (0 - 1 instead of 0-255).

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightAttenuation

<section name="Client" class="client" show="true">
This function sets setLightAttenuation value for both a pointlight and a spotlight.

``` lua
bool exports.dynamic_lighting:setLightAttenuation(element lightElement,float attenuation)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **float attenuation:** Value specifying how the light intensity changes over distance.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightFalloff

<section name="Client" class="client" show="true">
This function sets falloff value for a spotlight.

``` lua
bool exports.dynamic_lighting:setLightFalloff(element lightElement,float falloff)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **float falloff (radians):** Decrease in illumination between a spotlight's inner cone (the angle specified by Theta) and the outer edge of the outer cone (the angle specified by Phi).

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightTheta

<section name="Client" class="client" show="true">
This function sets theta value for a spotlight.

``` lua
bool exports.dynamic_lighting:setLightTheta(element lightElement,float theta)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **float theta (radians):** Angle, in radians, of a spotlight's inner cone - that is, the fully illuminated spotlight cone. This value must be in the range from 0 through the value specified by Phi.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightPhi

<section name="Client" class="client" show="true">
This function sets phi value for a spotlight.

``` lua
bool exports.dynamic_lighting:setLightPhi(element lightElement,float phi)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **float phi (radians):** Angle, in radians, defining the outer edge of the spotlight's outer cone. Points outside this cone are not lit by the spotlight. This value must be between 0 and pi.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightNormalShadowing

<section name="Client" class="client" show="true">
Determine if the light source should be obscured when lighting a surface on opposite angles.

``` lua
bool exports.dynamic_lighting:setLightNormalShadowing(element lightElement,bool normalShadow)
```

### Required Arguments

-   **element lightElement:** A previously declared light element.
-   **bool normalShadow:** Determine if the light source should be obscured when lighting a surface on opposite angles.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setShadersLayered

<section name="Client" class="client" show="true">
Should the main shader effects be created in a separate render pass ? As default only the vehicle effect is layered.

``` lua
bool exports.dynamic_lighting:setShadersLayered(bool isWorld, isVeh, isPed)
```

### Required Arguments

-   **bool isWorld, isVeh, isPed:** Should the shader effects be created in a separate render pass.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setGenerateBumpNormals

<section name="Client" class="client" show="true">
Should the shader effect generate bump normals from texture0. Doesn't work when normal shadowing is set to false.

``` lua
)
```

### Required Arguments

-   **bool isTrue:** Turn on or off bump mapping.

### Optional Arguments

-   **int textureSize:** The size of the input texture.
-   **float normalStrength.xyz:** How bumpy should the surface be ?

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightsDistFade

<section name="Client" class="client" show="true">
Set the Max distance of the light to sync and the distance on which the light starts to fade out.

``` lua
bool exports.dynamic_lighting:setLightsDistFade(int MaxEffectFade,int MinEffectFade)
```

### Required Arguments

-   **int MaxEffectFade:** Set the Max distance of the light to sync.(Must be greater than MinEffectFade and lower than maxEffectRange).
-   **int MinEffectFade:** Set the distance on which the light starts to fade out.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setLightsEffectRange

<section name="Client" class="client" show="true">
Set the Max distance from the camera the shader effects are applied to.

``` lua
bool exports.dynamic_lighting:setLightsEffectRange(int maxEffectRange)
```

### Required Arguments

-   **int maxEffectRange:** If non-zero, the shaders will be applied to textures nearer than maxDistance only.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setShaderForcedOn

<section name="Client" class="client" show="true">
Should the shader effect turn off when no lightsources.

``` lua
bool exports.dynamic_lighting:setShaderForcedOn(bool isShaderForcedOn)
```

### Required Arguments

-   **bool isShaderForcedOn:** Should the shader effect turn off when no lightsources.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setShaderTimeOut

<section name="Client" class="client" show="true">
Should the shader effect turn off after number of seconds (when no lightsources)

``` lua
bool exports.dynamic_lighting:setShaderTimeOut(int timeOut)
```

### Required Arguments

-   **int timeOut:** Should the shader effect turn off after number of seconds (when no lightsources)

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setShaderNightMod

<section name="Client" class="client" show="true">
Enable nightMod effect - requires proper manipulation of setTextureBrightness and SetShaderDayTime, also some additional shaders.

``` lua
bool exports.dynamic_lighting:setShaderNightMod(bool enable)
```

### Required Arguments

-   **bool enable:** Enable or disable nightMod effect

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setShaderDayTime

<section name="Client" class="client" show="true">
Another additional variable to control texture colors - requires setShaderNightMod(true)

``` lua
bool exports.dynamic_lighting:setShaderDayTime(float dayTime)
```

### Required Arguments

-   **float dayTime:** Another additional variable to control texture colors - requires setShaderNightMod(true) set 1 as default

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setShaderPedDiffuse

<section name="Client" class="client" show="true">
Enable or disable gta directional lights for ped.

``` lua
bool exports.dynamic_lighting:setShaderPedDiffuse(bool enable)
```

### Required Arguments

-   **bool enable:** Enable or disable gta directional lights for ped (enabled as default)

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setDirLightEnable

<section name="Client" class="client" show="true">
This function creates a vertex shader directional light. NOTE: Forcing the effects on or using any other lights is required for directional light to work.

``` lua
bool exports.dynamic_lighting:setDirLightEnable(bool enable = false)
```

### Required Arguments

-   **bool enable:** Enable or disable the directional light.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setDirLightDirection

<section name="Client" class="client" show="true">
This function sets the directional light direction.

``` lua
)
```

### Required Arguments

-   **float dirX,dirY,dirZ:** Direction that the light is pointing in world space. It's a vector as default.

### Optional Arguments

-   **bool isEuler:**Is the angle set as an “ZXY” euler andgle or a vector.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setDirLightColor

<section name="Client" class="client" show="true">
This function sets the directional light color value.

``` lua
bool exports.dynamic_lighting:setDirLightColor(float colorR,colorG,colorB,colorA)
```

### Required Arguments

-   **float colorR,colorG,colorB,colorA:** RGBA color emitted by the light (0 - 1 instead of 0-255).

### Returns

The function returns true if set successfully, false otherwise.

</section>
Examples
--------

``` lua
exports.dynamic_lighting:createPointLight(0,0,5,1,0,0,1,15)
```

This creates a red pointlight in world position (0,0,5)

Of course when you want to use these functions in your resources you have to include the dynamic\_lighting resource in meta.

See Also
--------

[Dynamic Lighting resource on MTA Community](http://community.multitheftauto.com/index.php?p=resources&s=details&id=9398)

[Light Types (Direct3D 9)](http://msdn.microsoft.com/en-us/library/windows/desktop/bb174697%28v=vs.85%29.aspx)

[Vehicle lights video](http://www.youtube.com/watch?v=2t_bje_XjUY)
