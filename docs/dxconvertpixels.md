This function converts [pixels](/docs/texture_pixels.md "wikilink") from one format to another.

Syntax
------

``` lua
string dxConvertPixels ( string pixels, string newFormat [, int quality = 80 ] )
```

### Required Arguments

-   **pixels :** The pixels to convert the format of
-   **newFormat :** The new format required (**'plain**' or **'png**' or **'jpeg**')

### Optional Arguments

-   **quality :** The quality of the returned pixels if the new format is **'jpeg**'

Returns
-------

Returns a copy of the pixels in the new format, or *false* if invalid arguments were passed to the function.

Example
-------

The code opens an image, read its pixels, convert the pixels to PNG, and then save it. (You can use [this](http://i1325.photobucket.com/albums/u630/Tourmalinelisa2/128x128.jpg) image to test.)

``` lua
addEventHandler('onClientResourceStart', resourceRoot, function()
  local img = fileOpen('img.jpg')
  local pixels = fileRead(img, fileGetSize(img))
  local pngPixels = dxConvertPixels(pixels, 'png')
  local newImg = fileCreate('img.png')
  fileWrite(newImg, pngPixels)
  fileClose(newImg)
  fileClose(img)
end)
```

Requirements
------------

See Also
--------
