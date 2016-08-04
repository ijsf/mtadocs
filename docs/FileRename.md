Renames the specified file.

**Note:** Also with this function you can move specified file to a new location, new folder or even to another resource's folder. But for this action executing resource must have 'ModifyOtherObjects' ACL right set to *true*.

Syntax
------

``` lua
bool fileRename ( string filePath, string newFilePath )
```

### Required Arguments

-   **filePath:** The [filepath](/filepath.md "wikilink") of the source file in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file. If the file is in the current resource, only the file path is necessary.
-   **newFilePath:** Destination [filepath](/filepath.md "wikilink") for the specified source file in the same format.

### Returns

If successful, returns *true*. Otherwise returns *false*.

Example
-------

This example renames the file *test1.txt* that is in the root of the current resource to *test2.txt*.

``` lua
if fileRename( "test1.txt", "test2.txt" ) then
    outputConsole("File `test1.txt` successfully renamed to `test2.txt`")
else
    outputConsole("Unable to rename `test1.txt`")
end
```

This example moves the file *test1.txt* that is in the root of the current resource to *myFolder* folder. If this folder is not exists, it will be created before moving the file *test1.txt*.

``` lua
if fileRename( "test1.txt", "myFolder/test1.txt" ) then
    outputConsole("File `test1.txt` successfuly moved to `myFolder` folder")
else
    outputConsole("Unable to move `test1.txt`")
end
```

See Also
--------
