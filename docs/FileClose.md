Closes a file handle obtained by [fileCreate](/fileCreate.md "wikilink") or [fileOpen](/fileOpen.md "wikilink").

Syntax
------

``` lua
bool fileClose ( file theFile )
```

### Required Arguments

-   **theFile:** The file handle to close.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

This example creates a text file and writes a string to it.

``` lua
local newFile = fileCreate("test.txt")                -- attempt to create a new file
if newFile then                                       -- check if the creation succeeded
    fileWrite(newFile, "This is a test file!")        -- write a text line
    fileClose(newFile)                                -- close the file once you're done with it
end
```

It is important to remember to close a file after you've finished all your operations on it, especially if you've been writing to the file. If you don't close a file and your resource crashes, all changes to the file may be lost.

See Also
--------
