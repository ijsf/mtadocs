Returns the current read/write position in the given file.

Syntax
------

``` lua
 int fileGetPos ( file theFile ) 
```

### Required Arguments

-   **theFile:** the file handle you wish to get the position of.

### Returns

Returns the file position if successful, or *false* if an error occured (e.g. an invalid handle was passed).

Example
-------

This example opens the file test.txt and outputs its contents and current read position to the console.

``` lua
local hFile = fileOpen("test.txt", true)       -- attempt to open the file (read only)
if hFile then                                  -- check if it was successfully opened
    local buffer
    while not fileIsEOF(hFile) do              -- as long as we're not at the end of the file...
        buffer = fileRead(hFile, 500)          -- ... read the next 500 bytes...
        outputConsole(buffer.."Current Position: "..fileGetPos(hFile))                  -- ... and output them to the console and outputs the current read position
    end
    fileClose(hFile)                           -- close the file once we're done with it
else
    outputConsole("Unable to open test.txt")
end
```

See Also
--------
