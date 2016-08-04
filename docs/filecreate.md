Creates a new file in a directory of a resource. If there already exists a file with the specified name, it is overwritten with an empty file.

Syntax
------

``` lua
file fileCreate ( string filePath )
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the file to be created in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if you want to create a file named 'myfile.txt' in the resource 'mapcreator', it can be created from another resource this way: *fileCreate(":mapcreator/myfile.txt")*.

If the file is in the current resource, only the file path is necessary, e.g. *fileCreate(“myfile.txt”)*.

### Returns

If successful, returns a file handle which can be used with other file functions ([fileWrite](/docs/filewrite.md "wikilink"), [fileClose](/fileClose.md "wikilink")...). Returns *false* if an error occured.

Example
-------

This example creates a text file in the current resource and writes a string to it.

``` lua
local newFile = fileCreate("test.txt")                -- attempt to create a new file
if (newFile) then                                       -- check if the creation succeeded
    fileWrite(newFile, "This is a test file!")        -- write a text line
    fileClose(newFile)                                -- close the file once you're done with it
end
```

Notice that you can't simply do *fileWrite(“test.txt”, “File content”)*. Instead, file functions operate on a **file handle**, which is a special object representing an open file. *fileCreate* creates a file, opens it, and returns the resulting handle.

It is also important to remember to close a file after you've finished all your operations on it, especially if you've been writing to the file. If you don't close a file and your resource crashes, all changes to the file may be lost. If the file already exists, a new file will be created on local.

See Also
--------
