This function gets the position of the camera and the position of the point it is facing.

Note: The server-side version of this function returns the last camera matrix that was set by the server, and thus does not necessarily indicate the current matrix of the camera (since it may have been changed client-side).

Procedural
----------

<section name="Server" class="server" show="true">
``` lua
float float float float float float float float getCameraMatrix (player thePlayer)
```

### Required Arguments

-   **thePlayer:** The player whose camera matrix is to be returned.

</section>
<section name="Client" class="client" show="true">
``` lua
float float float float float float float float getCameraMatrix ()
```

</section>
This function returns 8 [floats](/docs/float.md "wikilink") if the argument is valid (when applicable); the first three indicate the position of the camera, the next three indicate the position of the point it's facing, and the last two are the roll and field of view. Returns *false* if the argument is invalid.

### Example

<section name="Client" class="client" show="true">
``` lua
local x, y, z, lx, ly, lz = getCameraMatrix ()
x, lx = x + 1, lx + 1

setCameraMatrix (x, y, z, lx, ly, lz)
```

</section>
See Also
--------
