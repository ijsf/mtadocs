Opens an existing file for reading and writing.

Syntax
------

``` lua
file fileOpen ( string filePath [, bool readOnly = false ])
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the file in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if there is a file named 'coolObjects.txt' in the resource 'objectSearch', it can be opened from another resource this way: *fileOpen(":objectSearch/coolObjects.txt")*.

If the file is in the current resource, only the file path is necessary, e.g. *fileOpen(“coolObjects.txt”)*.

### Optional Arguments

-   **readOnly:** By default, the file is opened with reading and writing access. You can specify *true* for this parameter if you only need reading access.

### Returns

If successful, returns a file handle for the file. Otherwise returns *false* (f.e. if the file doesn't exist).

Example
-------

This example opens the file test.txt that is in the root of the current resource, and outputs its contents to the console.

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

This example show how to append data to an existing file:

``` lua
local hFile = fileOpen("test.txt")             -- attempt to open the file (read and write mode)
if hFile then                                  -- check if it was successfully opened
    fileSetPos( hFile, fileGetSize( hFile ) )  -- move position to the end of the file
    fileWrite(hFile, "hello" )                 -- append data
    fileClose(hFile)                           -- close the file once we're done with it
else
    outputConsole("Unable to open test.txt")
end
```

See Also
--------
