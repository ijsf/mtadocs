This function forces a client to capture the current screen output and send it back to the server. The image will contain the GTA HUD and the output of any dxDraw functions that are not flagged as 'post GUI'. The image specifically excludes the chat box and all GUI (including the client console). The result is received with the event [onPlayerScreenShot](/onPlayerScreenShot.md "wikilink").

Syntax
------

``` lua
bool takePlayerScreenShot( player thePlayer, int width, int height [ , string tag = "", int quality = 30, int maxBandwith = 5000 ] )         
```

### Required Arguments

-   **thePlayer:** the player to get the screen capture from.
-   **width:** the width of the capture image.
-   **height:** the height of the capture image.

### Optional Arguments

-   **tag :** A string to help identify the screen capture. The string is passed to the matching [onPlayerScreenShot](/onPlayerScreenShot.md "wikilink") event for your personal convenience.
-   **quality :** Quality of the final JPEG image from 0 to 100. A lower value can reduce the memory used by the image considerably which will result in faster and less intrusive uploads.
-   **maxBandwith :** The amount of client upload bandwidth to use (in bytes per second) when sending the image.

### Returns

Returns *true* if the function was successfully, *false* if invalid arguments are specified.

Example
-------

This example will initiate a capture of a Random Players screen

``` lua
local player = getRandomPlayer()
takePlayerScreenShot( player, 320, 240 )
```

Requirements
------------

See Also
--------
