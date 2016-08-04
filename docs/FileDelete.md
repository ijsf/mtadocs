Deletes the specified file.

Syntax
------

``` lua
bool fileDelete ( string filePath )
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the file to delete in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if you want to delete a file name “myFile.txt” in the resource 'fileres', it can be deleted from another resource this way: *fileDelete(":fileres/myFile.txt")*.

If the file is in the current resource, only the file path is necessary, e.g. *fileDelete(“myFile.txt”)*.

### Returns

Returns *true* if successful, *false* otherwise (for example if there exists no file with the given name, or it does exist but is in use).

Example
-------

This example will show us how to create a file “text.txt” spell it “This is a test file!”, Close the file and delete it:

``` lua
local newFile = fileCreate("test.txt")                -- attempt to create a new file
if (newFile) then                                     -- check if the creation succeeded
    fileWrite(newFile, "This is a test file!")        -- write a text line
    fileClose(newFile)                                -- close the file once you're done with it
    fileDelete(newFile)                               -- delete file
end
```

See Also
--------
