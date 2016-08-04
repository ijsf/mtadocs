This function gets the dimensions of [pixels](/docs/texture_pixels.md "wikilink") contained in a string. It works with all pixel formats.

Syntax
------

``` lua
int int dxGetPixelsSize ( string pixels )
```

### Required Arguments

-   **pixels :** The pixels to get the dimensions of

Returns
-------

Returns width and height of the pixels if successful, *false* if invalid arguments were passed to the function.

Example
-------

The example loads an image, gets its pixels, and outputs the pixels size. (You can use [this](http://i1325.photobucket.com/albums/u630/Tourmalinelisa2/128x128.jpg) image to test.)

``` lua
addEventHandler('onClientResourceStart', resourceRoot, function()
  local img = fileOpen('img.jpg')
  local pixels = fileRead(img, fileGetSize(img))
  local size = dxGetPixelsSize(pixels)
  outputChatBox('Pixels size is: ' .. size)
  fileClose(img)
end)
```

Requirements
------------

See Also
--------
