Syntax
------

``` lua
string fileGetPath ( file theFile )
```

### Required Arguments

-   **theFile:** The file you want to get the path.

### Returns

Returns a *string* with the path, *false* if there's something wrong with the file in the argument.

Example
-------

``` lua
local newFile = fileCreate("test.txt")                -- attempt to create a new file
if (newFile) then                                       -- check if the creation succeeded
    local path = fileGetPath(newFile)
    outputChatBox("New file created at: "..path,root,0,255,0)
    fileClose(newFile)                                -- close the file once you're done with it
end
```

See Also
--------
