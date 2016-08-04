Reads the specified number of bytes from the given file starting at its current read/write position, and returns them as a string.

Syntax
------

``` lua
string fileRead ( file theFile, int count )
```

### Required Arguments

-   **theFile:** A handle to the file you wish to read from. Use [fileOpen](/docs/fileOpen.md "wikilink") to obtain this handle.
-   **count:** The number of bytes you wish to read.

### Returns

Returns the bytes that were read in a string. Note that this string might not contain as many bytes as you specified if an error occured, i.e. end of file.

Example
-------

This example opens the file test.txt and outputs its contents to the console.

``` lua
local hFile = fileOpen("test.txt")             -- attempt to open the file
if hFile then                                  -- check if it was successfully opened
    local buffer
    while not fileIsEOF(hFile) do              -- as long as we're not at the end of the file...
        buffer = fileRead(hFile, 500)          -- ... read the next 500 bytes...
        outputConsole(buffer)                  -- ... and output them to the console
    end
    fileClose(hFile)                           -- close the file once we're done with it
else
    outputConsole("Unable to open test.txt")
end
```

[fileOpen](/docs/fileOpen.md "wikilink") sets the read/write position to the beginning of the file. Each call of fileRead will read 500 bytes from the current position, and advance the position over the same amount. If we get near the end of the file and there are less than 500 bytes left to read, all that's left will be read and [fileIsEOF](/fileIsEOF.md "wikilink") will return *true*.

See Also
--------
