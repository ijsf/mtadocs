This function returns the minimum and maximum coordinates of an element's bounding box.

It should be noted that the values returned are relative to the position of the element, and as such if you wish to get world coordinates for drawing, et etcetera, you should retrieve the position of the element and add the returned values onto that.

**Note:** The element must be streamed in for this function to work.

Syntax
------

``` lua
float float float float float float getElementBoundingBox ( element theElement )
```

### Required Arguments

**theElement:** the element whose bounding box we want to get.

### Returns

-   Returns *min x, min y, min z, max x, max y, max z* if the passed element is valid and streamed in, *false* otherwise.

Example
-------

This example outputs to chatbox the minimum and the maximum coordinates of an element.

``` lua
function minMaxOutput ( theElement )
    local x0, y0, z0, x1, y1, z1 = getElementBoundingBox ( theElement )
    if ( x0 ) then
        outputChatBox ( "The coords are: " .. x0 .. ", " .. y0 .. ", " .. z0 .. ", " .. x1 .. ", " .. y1 .. ", " .. z1 )
    else
        outputChatBox ( "Failed to retrieve bounding box" )
    end
end
```

See Also
--------
