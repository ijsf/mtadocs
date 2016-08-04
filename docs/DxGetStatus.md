This function gets information about various internal datum

Syntax
------

``` lua
table dxGetStatus ( )
```

### Returns

Returns a table with the following entries:

-   **TestMode :** The current dx test mode. See [dxSetTestMode](/dxSetTestMode.md "wikilink").
-   **VideoCardName :** The name of the graphics card.
-   **VideoCardRAM :** The installed memory in MB of the graphics card.
-   **VideoCardPSVersion :** The maximum pixel shader version of the graphics card.
-   **VideoCardNumRenderTargets:** The maximum number of simultaneous render targets a shader can use.
-   **VideoCardMaxAnisotropy:** The maximum anisotropic filtering available. (0-4 which respectively mean: off,2x,4x,8x,16x)
-   **VideoMemoryFreeForMTA :** The amount of memory in MB available for MTA to use. **When this gets to zero, [guiCreateFont](/guiCreateFont.md "wikilink"), [dxCreateFont](/dxCreateFont.md "wikilink") and [dxCreateRenderTarget](/dxCreateRenderTarget.md "wikilink") will fail.**
-   **VideoMemoryUsedByFonts :** The amount of graphic memory in MB used by custom fonts.
-   **VideoMemoryUsedByTextures :** The amount of graphic memory in MB used by textures.
-   **VideoMemoryUsedByRenderTargets :** The amount of graphic memory in MB used by render targets.
-   **SettingWindowed :** The windowed setting. (true/false)
-   **SettingFXQuality :** The FX Quality. (0-3)
-   **SettingDrawDistance :** The draw distance setting. (0-100)
-   **SettingVolumetricShadows :** The volumetric shadows setting. (true/false)
-   **SettingStreamingVideoMemoryForGTA :** The usable graphics memory setting. (64-256)
-   **SettingAnisotropicFiltering:** The anisotropic filtering setting. (0-4 which respectively mean: off,2x,4x,8x,16x)
-   **SettingAntiAliasing:** The anti-aliasing setting. (0-3 which respectively mean: off,1x,2x,3x)
-   **SettingHeatHaze:** The heat haze setting. (true/false)
-   **SettingGrassEffect:** The grass effect setting. (true/false)
-   **Setting32BitColor:** The color depth of the screen. (false is 16bit, true is 32bit)
-   **SettingHUDMatchAspectRatio:** The hud match aspect ratio setting (true/false)
-   **SettingAspectRatio:** The aspect ratio setting (“auto”, “4:3”, “16:10”, “16:9”)
-   **SettingFOV:** The FOV setting
-   **AllowScreenUpload :** The allows screen uploads setting. (true/false)
-   **DepthBufferFormat:** The format of the shader readable depth buffer, or 'unknown' if not available
-   **UsingDepthBuffer:** *true* if the depth buffer is used, *false* otherwise

Example
-------

``` lua
addCommandHandler( "getinfo",
    function( )
        local info = dxGetStatus( )
        for k, v in pairs( info ) do
            outputChatBox( k .. " : " .. tostring( v ) )
        end
    end
)
```

Changelog
---------

See Also
--------
