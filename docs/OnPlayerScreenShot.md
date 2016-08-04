This event is triggered when the screen capture requested by [takePlayerScreenShot](/takePlayerScreenShot.md "wikilink") has completed.

Parameters
----------

``` lua
resource theResource, string status, string imageData, int timestamp, string tag
```

-   **theResource**: The resource which called [takePlayerScreenShot](/takePlayerScreenShot.md "wikilink")
-   **status**: The status of the event which can be one of three values:
    -   *“ok”* - The image capture was successful and imageData will contain a JPEG image.
    -   *“disabled”* - The image capture failed because the player has disabled screen uploads.
    -   *“minimized”* - The image capture failed because the player has minimized the screen. (i.e. alt-tabbed)
-   **imageData**: A string which contains the JPEG image data. This can be saved with the file functions, or sent to players with triggerClientEvent or even uploaded to a web site.
-   **timestamp**: The server tick count when the capture was taken.
-   **tag**: The tag string passed to [takePlayerScreenShot](/takePlayerScreenShot.md "wikilink").

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink")

Example
-------

This example captures the screen of a random player every 2 seconds and shows it to everyone:

<section name="Server" class="server" show="true">
``` lua
--------------------------------------------------
-- Take screen shot every 2 seconds
function doTakeScreenShot()
    takePlayerScreenShot( getRandomPlayer(), 320, 200 )
end
setTimer(doTakeScreenShot, 2000, 0)

--------------------------------------------------
-- Receive screen shot result
addEventHandler( "onPlayerScreenShot", root,
    function ( theResource, status, pixels, timestamp, tag )
        triggerClientEvent( root, "onMyClientScreenShot", resourceRoot, pixels )  -- Relay to all players
    end
)
```

</section>
<section name="Client" class="client" show="true">
``` lua
--------------------------------------------------
-- Turn image data into a texture at the client
addEvent("onMyClientScreenShot",true)
addEventHandler( "onMyClientScreenShot", resourceRoot,
    function( pixels )
        if image then
            destroyElement(image)
        end
        image = dxCreateTexture( pixels )
    end
)

--------------------------------------------------
-- Show image
addEventHandler( "onClientRender", root,
    function()
        if image then
            dxDrawImage( 100, 250, 320, 200, image )
        end
    end
)
```

</section>
Requirements
------------
