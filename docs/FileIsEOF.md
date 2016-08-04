Checks if the file position is at the end of the file.

Syntax
------

``` lua
bool fileIsEOF ( file theFile )
```

### Required Arguments

-   **theFile:** A handle to the file you wish to check.

### Returns

Returns *true* if the file position of the specified file is at the end of the file, *false* otherwise.

Example
-------

This example opens the file test.txt and outputs its contents to the console.

``` lua
local hFile = fileOpen("test.txt", true)       -- attempt to open the file (read only)
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

When you open a file, its file position is set to the beginning of the file. Each call to [fileRead](/fileRead.md "wikilink") or [fileWrite](/fileWrite.md "wikilink") moves the position ahead by the amount of bytes that were read/written. This way, by using *fileIsEOF* you can check if you've passed through the whole file.

See Also
--------
