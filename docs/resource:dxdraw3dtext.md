This resource allowe you to draw 3D-DX texts any where in the game .

How it works
------------

You only need to use the exported function from the resource **dxDraw3DText** and draw the text . ( To use the exported function use [call](/docs/call.md "wikilink") function ) .

The dxDraw3DText function
-------------------------

### Syntax

``` lua
 )
```

### Required Arguments

-   **text :** A [string](/docs/string.md "wikilink") representing the text you wish to draw .
-   **x, y, z :** Three integers representing the world coordinates of where you want the text to be .

### Optional Arguments

-   **scale :** An [int](/docs/int.md "wikilink") representing the size of the font .
-   **font :** A [string](/docs/string.md "wikilink") representing the font type, This CAN'T be a [DX font](/DX_font.md "wikilink") element, It can ONLY be :

-   **r, g, b :** Three integers representing the RGB Color codes for the text .
-   *' maxDistance :*' An [int](/docs/int.md "wikilink") representing the max distance the text will show in .

### Returns

The function returns a *text element* if successfule, *false* otherwise .

### Example

This example will draw a 3D text neer a player when the resource starts, And destroys it after 5 secinds .

``` lua
local dxDraw3DText = exports.3D_DX_Texts:dxDraw3DText -- define the function

addEventHandler( "onClientResourceStart", getResourceRootElement( getThisResource( ) ),
    function( )
        local x, y, z = getElementPosition( getLocalPlayer( ) ) -- getting the player coordinates
        local playerName = getPlayerName( getLocalPlayer( ) ) -- getting the player name
        local theText = dxDraw3DText( "Welcome " .. playerName, x, y, z ) -- dtawing the text
        if theText then -- if it was drawn
            setTimer( destroyElement, 5000, 1, theText ) -- set a time to destroy it after 5 seconds
        end
    end
)
```

Notes
-----

-   The *dxDraw3DText* function is client side only .
-   The *dxDraw3DText* function doesn't need the [onClientRender](/docs/onClientRender.md "wikilink") event to work .
-   The *dxDraw3DText* function only creates a *text element*, The drawing and stuff is done in the resource, So it MUST be running so the texts show .

Download
--------

You can download the resource, comment about it, rate it and report any bugs at the community page : [1](https://community.multitheftauto.com/index.php?p=resources&s=details&id=7613)
