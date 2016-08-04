This function sets the amount of geometric sub-division to use when drawing a [shader](/docs/shader.md "wikilink") element with [dxDrawImage](/dxDrawImage.md "wikilink").

Using tessellation allows a shader to manipulate the shape of the rendered image at each sub-division boundary.

Syntax
------

``` lua
bool dxSetShaderTessellation ( element theShader, int tessellationX, int tessellationY )
```

### Required Arguments

-   **theShader:** The shader element whose tessellation is to be changed
-   **tessellationX:** The number of sub-division points along the X axis. Range is 1 to 500.
-   **tessellationY:** The number of sub-division points along the Y axis. Range is 1 to 500.

### Returns

Returns *true* if the shader element's tessellation was successfully changed, *false* otherwise.

Example
-------

``` lua
myShader = dxCreateShader( "hello.fx" )
dxSetShaderTessellation ( myShader, 16, 16 )
```

Requirements
------------

See Also
--------
