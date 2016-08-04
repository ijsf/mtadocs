Writes one or more strings to a given file, starting at the current read/write position. Advances the position over the number of bytes that were written.

Syntax
------

``` lua
int fileWrite ( file theFile, string string1 [, string string2, string string3 ...])
```

### Required Arguments

-   **theFile:** A handle to the file you wish to write to. The file must have been opened with write access, i.e. the file handle must be a result of [fileCreate](/docs/fileCreate.md "wikilink") or [fileOpen](/fileOpen.md "wikilink") with the readonly parameter set to *false*.
-   **string1:** The string to write.

### Optional Arguments

-   You can provide any number of additional strings to write after **string1**. These will be written in the order in which they are specified.

### Returns

Returns the number of bytes successfully written to the file, returns *false* if invalid arguments were specified.

Example
-------

This example creates a text file and writes a string to it.

``` lua
local fileHandle = fileCreate("test.txt")             -- attempt to create a new file
if fileHandle then                                    -- check if the creation succeeded
    fileWrite(fileHandle, "This is a test file!")     -- write a text line
    fileClose(fileHandle)                             -- close the file once you're done with it
end
```

Notice that you can't simply do fileWrite(“test.txt”, “File content”). Instead, file functions operate on a **file handle**, which is a special object representing an open file.

It is also important to remember to close a file after you've finished all your operations on it, especially if you've been writing to the file. If you don't close a file and your resource crashes, all changes to the file may be lost.

See Also
--------
