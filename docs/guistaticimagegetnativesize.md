This function gets the native size of image. That means the original size in pixels of the image file.

Syntax
------

``` lua
int int guiStaticImageGetNativeSize ( element theImage )
```

### Required Arguments

-   **theImage:** The static image element to get the original size of.

### Returns

Returns two integers where first is the width and second the height of the image in pixels, *false* if the image element was invalid.

Example
-------

This example creates an image at the resource's start and changes its size to the original size so it keeps the best quality.

    [lua]
    addEventHandler("onClientResourceStart", resourceRoot,
        function ()
            local image = guiCreateStaticImage(200, 200, 10, 10, "image.png", false) --Creates image at 200x200 point on screen
            local x, y = guiStaticImageGetNativeSize(image) --Gets the original size
            guiSetSize(image, x, y, false) --Sets the size to native one
        end)

See Also
--------
