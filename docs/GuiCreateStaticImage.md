This function creates a static image using a .png image in the resource.

Syntax
------

``` lua
element guiCreateStaticImage ( float x, float y, float width, float height, string path, bool relative, [element parent = nil] )
```

### Required Arguments

[frame|Example GUI static image.](/Image:gui-staticimage.png.md "wikilink")

-   **x:** A float of the 2D x position of the image on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the image on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the image. This is affected by the *relative* argument.
-   **height:** A float of the height of the image. This is affected by the *relative* argument.
-   **path:** The [filepath](/filepath.md "wikilink") of the image file that is being loaded.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the image is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns [element](/element.md "wikilink") if image was created successfully, *false* otherwise.

Example
-------

This example will display an image (imagename.png) on the client's (player's) screen.

<section name="Client-side script (example.lua)" class="client" show="true">
    [lua]
    function showClientImage()
       guiCreateStaticImage( 20, 200, 100, 100, "imagename.png", false )
    end
    addEventHandler( "onClientResourceStart", getResourceRootElement( getThisResource() ), showClientImage )

</section>
<section name="meta.xml" class="server" show="true">
In this example [Meta.xml](/Meta.xml.md "wikilink") is used to tell the server which files it will be using.

``` xml
<meta>
  <info author="Yourname" version="1.0" />
  <script src="example.lua" type="client" />
  <file src="imagename.png" />
</meta>
```

</section>
See Also
--------
