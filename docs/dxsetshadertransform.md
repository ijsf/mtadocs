This function applies a 3D transformation to a [shader](/docs/shader.md "wikilink") element when it is drawn with [dxDrawImage](/docs/dxdrawimage.md "wikilink").

Syntax
------

``` lua
bool dxSetShaderTransform ( element theShader,
                            float rotationX, float rotationY, float rotationZ,
                          [ float rotationCenterOffsetX = 0, float rotationCenterOffsetY = 0, float rotationCenterOffsetZ = 0,
                            bool bRotationCenterOffsetOriginIsScreen = false,
                            float perspectiveCenterOffsetX = 0, float perspectiveCenterOffsetY = 0,
                            bool bPerspectiveCenterOffsetOriginIsScreen = false ] )
```

### Required Arguments

-   **theShader:** The shader element whose transformation is to be changed
-   **rotationX:** Rotation angle in degrees around the X axis (Left,right). This will make the shader rotate along its width.
-   **rotationY:** Rotation angle in degrees around the Y axis (Up,down). This will make the shader rotate along its height.
-   **rotationZ:** Rotation angle in degrees around the Z axis (In,out). This will make the shader rotate in a similar way to the rotation argument in [dxDrawImage](/docs/dxdrawimage.md "wikilink").

### Optional Arguments

-   **rotationCenterOffsetX :** The center of rotation offset X position in screen relative units.
-   **rotationCenterOffsetY :** The center of rotation offset Y position in screen relative units.
-   **rotationCenterOffsetZ :** The center of rotation offset Z position in screen relative units.
-   **bRotationCenterOffsetOriginIsScreen :** Set to [true](/docs/boolean.md "wikilink") if the center of rotation origin should be the center of the screen rather than the center of the image.
-   **perspectiveCenterOffsetX :** The center of perspective offset X position in screen relative units.
-   **perspectiveCenterOffsetY :** The center of perspective offset Y position in screen relative units.
-   **bPerspectiveCenterOffsetOriginIsScreen :** Set to [true](/docs/boolean.md "wikilink") if the center of perspective origin should be the center of the screen rather than the center of the image.

To convert screen relative units into screen pixel coordinates, *multiply* by the screen size. Conversely, to convert screen pixel coordinates to screen relative units, ***divide*** by the screen size.

### Returns

Returns *true* if the shader element's transform was successfully changed, *false* otherwise.

Example
-------

``` lua
```

Requirements
------------

See Also
--------
