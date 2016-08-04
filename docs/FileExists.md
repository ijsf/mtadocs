This functions checks whether a specified file exists inside a resource.

Syntax
------

``` lua
bool fileExists ( string filePath )
```

### Required Arguments

-   **filePath:** The [filepath](/filepath.md "wikilink") of the file, whose existence is going to be checked, in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is checked to be in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if you want to check whether a file named 'myfile.txt' exists in the resource 'mapcreator', it can be done from another resource this way: *fileExists(":mapcreator/myfile.txt")*.

If the file, whose existence is going to be checked, is in the current resource, only the file path is necessary, e.g. *fileExists(“myfile.txt”)*.

### Returns

Returns *true* if the file exists, *false* otherwise.

Example
-------

This example checks if a file exists in a resource directory

``` lua
function checkExistingFile(player,cmd,filename,resourcename)
    if not filename then -- if the player didn't include a filename
        outputChatBox("ERROR: Syntax '/checkfile filename resourcename(optional)'.",player) -- display error
        return false  -- stop function
    end
    if not resourcename then -- if the player didn't specify the resource he wants to check, use current resource
        resourcename = getResourceName(resource) --every resource has a predefined global variable called resource that contains the resource pointer for that resource, in other words, the value that getThisResource() function returns.
    else
        if not getResourceFromName(resourcename) then -- if a resource with that name doesn't exist, output error and stop function
            outputChatBox("ERROR: Resource "..resourcename.." doesn't exist.",player) -- output error message
            return false -- stop the function here
        end
    end
    -- as it hasn't stopped anywhere, we have both correct resourcename and filename
    local exists = fileExists((":%s/%s"):format(resourcename,filename)) -- using shorter format of string.format, see StringLibraryTutorial in lua wiki for that
    if exists then
        outputChatBox(("The file %q in resource %q exists"):format(filename,resourcename))
    else
        outputChatBox(("The file %q in resource %q doesn't exist"):format(filename,resourcename))
    end
end
addCommandHandler("exists",checkExistingFile)
```

See Also
--------
