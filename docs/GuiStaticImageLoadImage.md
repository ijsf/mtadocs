This function allows you to change the image in GUI static image element to another one.

Syntax
------

``` lua
bool guiStaticImageLoadImage ( element theElement, string filename )
```

### Required Arguments

-   **theElement:** The static image element to be changed.
-   **filename:** A string specifying the [filepath](/docs/filepath.md "wikilink") of the image file being loaded in current resource.

### Returns

Returns *true* if the the image in the static image element was successfully changed, *false* otherwise.

Example
-------

This example creates a static image (myimage.png) and replaces it with other image (otherimage.png) 10 seconds after creation.

<section name="Client-side script (example.lua)" class="client" show="true">
    [lua]
    local myImage = guiCreateStaticImage ( 0.45, 0.48, 0.2, 0.5, "myimage.png", true )
    setTimer ( guiStaticImageLoadImage, 10000, 1, myImage, "otherimage.png" )

</section>
<section name="meta.xml" class="server" show="true">
In this example meta.xml is used to tell the server which files it will be using.

``` xml
<meta>
<info author="Yourname" version="1.0" />
<script src="example.lua" type="client" />
<file src="myimage.png" />
<file src="otherimage.png" />
</meta>
```

</section>
See Also
--------
