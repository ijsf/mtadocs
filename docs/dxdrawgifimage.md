<lowercasetitle></lowercasetitle>

This function simulates the effect of a GIF image by using image sprites.

Syntax
------

``` lua
element dxDrawGifImage ( float x, float y, float width, float height, string path, float startImageID, string fileExtension, float effectSpeed )
```

### Required Arguments

-   **x:** A float of the 2D x position of the GUI button on a player's screen.
-   **y:** A float of the 2D y position of the GUI button on a player's screen.
-   **width:** A float of the width of the GUI button.
-   **height:** A float of the height of the GUI button.
-   **path:** The filepath of the image files will be loaded. A "%s" is required to denote where the “id” is placed.

`   "%snyancat.png" would be read as `“`1nyancat.png`”` `“`2nyancat.png`”` etc`
`   `“`a%sbcdefghe`”` would read the images `“`a1sbcdefghe`”` `“`a2sbcdefghe`”` `“`a3sbcdefghe`”` etc.`

-   **startImageID:** The image ID that will be loaded in the first place.
-   **fileExtension:** The image extension ( e.g: png, jpg, etc. ).
-   **effectSpeed:** The speed between the change of the images.

Code
----

<section name="Clientside Script" class="client" show="true">
``` lua
function dxDrawGifImage ( x, y, w, h, path, iStart, iType, effectSpeed )
    local gifElement = createElement ( "dx-gif" )
    if ( gifElement ) then
        setElementData (
            gifElement,
            "gifData",
            {
                x = x,
                y = y,
                w = w,
                h = h,
                imgPath = path,
                startID = iStart,
                imgID = iStart,
                imgType = iType,
                speed = effectSpeed,
                tick = getTickCount ( )
            },
            false
        )
        return gifElement
    else
        return false
    end
end

addEventHandler ( "onClientRender", root,
    function ( )
        local currentTick = getTickCount ( )
        for index, gif in ipairs ( getElementsByType ( "dx-gif" ) ) do
            local gifData = getElementData ( gif, "gifData" )
            if ( gifData ) then
                if ( currentTick - gifData.tick >= gifData.speed ) then
                    gifData.tick = currentTick
                    gifData.imgID = ( gifData.imgID + 1 )
                    if ( fileExists ( gifData.imgPath .."".. gifData.imgID ..".".. gifData.imgType ) ) then
                        gifData.imgID = gifData.imgID
                        setElementData ( gif, "gifData", gifData, false )
                    else
                        gifData.imgID = gifData.startID
                        setElementData ( gif, "gifData", gifData, false )
                    end
                end
                dxDrawImage ( gifData.x, gifData.y, gifData.w, gifData.h, gifData.imgPath .."".. gifData.imgID ..".".. gifData.imgType )
            end
        end
    end
)
```

</section>
Example
-------

<section name="Client" class="client" show="true">
This example will create a “gif” image and a command to destroy it.

``` lua
gif = dxDrawGifImage ( 769, 175, 193, 145, "images/flag_arg", 0, "png", 120 )

addCommandHandler ( "destroygif",
    function ( )
        destroyElement ( gif )
    end
)
```

</section>
Author: Castillo

See Also
--------
