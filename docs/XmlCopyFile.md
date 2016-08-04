This function copies all contents of a certain node in a XML document to a new document file, so the copied node becomes the new file's root node. The new file will not be saved to file system until [xmlSaveFile](/xmlSaveFile.md "wikilink")() is called

Syntax
------

``` lua
xmlnode xmlCopyFile ( xmlnode nodeToCopy, string newFilePath )
```

### Required Arguments

-   **nodeToCopy:** the [xmlnode](/xmlnode.md "wikilink") that is to be copied to a new document.
-   **newFilePath:** the path of the file that is to be created, in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file.

  
For example, to create a file named 'newfile.xml' with myNode as the root node in the resource 'ctf', it can be done from another resource this way: *xmlCopyFile(myNode, ":ctf/newfile.xml")*.

If the file is to be in the current resource, only the file path is necessary, e.g. *xmlCopyFile(myNode, “newfile.xml”)*.

### Returns

Returns the [xmlnode](/xmlnode.md "wikilink") of the copy if the node was successfully copied, *false* if invalid arguments were passed.

Example
-------

In this example we will load an xml file (in the example config.xml) and create a copy in a new folder with the name of copy-config.xml:

``` lua
local config = xmlLoadFile("config.xml")
-- create a copy of xml structure in memory
local newFile = xmlCopyFile(config, "copy/copy-config.xml")
if newFile then
  -- write this new copy to a filesystem
  xmlSaveFile(newFile)
end
-- unload config xml node from memory if it will not be used anytime soon
xmlUnloadFile(config)
```

See Also
--------

[ru:xmlCopyFile](/ru:xmlCopyFile.md "wikilink")
