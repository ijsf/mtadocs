This function returns the format of [pixels](/docs/texture_pixels.md "wikilink") contained in a string.

Syntax
------

``` lua
string dxGetPixelsFormat ( string pixels )
```

### Required Arguments

-   **pixels :** The pixels to get the format of

Returns
-------

Returns the format of the pixels if successful (**'plain**' or **'png**' or **'jpeg**'), *false* if invalid arguments were passed to the function.

Example
-------

The example loads an image, gets its pixels, and outputs the pixels format. (You can use [this](http://i1325.photobucket.com/albums/u630/Tourmalinelisa2/128x128.jpg) image to test.)

``` lua
addEventHandler('onClientResourceStart', resourceRoot, function()
  local img = fileOpen('img.jpg')
  local pixels = fileRead(img, fileGetSize(img))
  local pixelsFormat = dxGetPixelsFormat(pixels)
  outputChatBox('Pixels format is: ' .. pixelsFormat)
  fileClose(img)
end)
```

Requirements
------------

See Also
--------
