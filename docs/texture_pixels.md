#### Pixels

------------------------------------------------------------------------

**\*** MTA refers to the raw information that a [texture](/docs/texture.md "wikilink") contains as 'pixels'.

**\*** Pixels can be retrieved from any [texture](/docs/texture.md "wikilink") type including [render targets](/dxCreateRenderTarget.md "wikilink") and [screen sources](/dxCreateScreenSource.md "wikilink") by using the function [dxGetTexturePixels](/dxGetTexturePixels.md "wikilink").

**\*** Pixels are just a string to Lua, so they can be saved to a file or even sent over the 'internet'.

#### Pixels properties

------------------------------------------------------------------------

Pixels have two properties:

-   **dimensions** (width and height) which is retrieved by using the function [dxGetPixelsSize](/docs/dxGetPixelsSize.md "wikilink")
-   **format** (plain,jpeg,png) which is retrieved by using the function [dxGetPixelsFormat](/docs/dxGetPixelsFormat.md "wikilink")
    -   *plain* - Fastest and simplest - It's the format of the pixels returned by [dxGetTexturePixels](/docs/dxGetTexturePixels.md "wikilink") and the only one that can be used with [dxSetTexturePixels](/dxSetTexturePixels.md "wikilink"), [dxGetPixelColor](/dxGetPixelColor.md "wikilink") and [dxSetPixelColor](/dxSetPixelColor.md "wikilink"). But it also uses a lot of bytes, so internet transfers will be longer. Also can't be read by Photoshop or browsers etc.
    -   *png* - A few less bytes, still quite big for net transfers. Can be saved to a file and read by Photoshop and browsers etc.
    -   *jpeg* - A lot less bytes, so best for net transfers. Can be saved to a file and read by Photoshop and browsers etc.

To convert between the 3 different formats, use the function [dxConvertPixels](/docs/dxConvertPixels.md "wikilink")

#### Pixels more

------------------------------------------------------------------------

Pixels can also be loaded from any png/jpeg file just like this:

`   fh = fileOpen( `“`hello.jpg`”` )`
`   pixels = fileRead(fh,fileGetSize ( fh ))`
`   fileClose(fh)`

Pixels can be used to create textures just like this:

`   myNewTexture = dxCreateTexture(pixels)`

Pixels can be used to save textures just like this:

`   pixels = dxGetTexturePixels(myRenderTarget)`
`   pixels = dxConvertPixels(pixels, 'jpeg')`
`   fh = fileCreate( `“`piccy.jpg`”` )`
`   fileWrite(fh, pixels)`
`   fileClose(fh)`

#### Pixels performance

------------------------------------------------------------------------

Getting/setting pixels from textures is not quick and not something you want to be doing every frame (in onClientRender for example). Setting pixels to a render target is especially slow. Pixels are ideal however for transferring composite images built on a render target into a normal texture for later use. For example, making a custom radar map.
