This function creates a new XML document, which can later be saved to a file by using [xmlSaveFile](/docs/xmlsavefile.md "wikilink"). This function will overwrite the file specified if it already exists.

Syntax
------

``` lua
xmlnode xmlCreateFile ( string filePath, string rootNodeName )
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the file in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file will be in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if you want to create a file named 'new.xml' in the resource 'ctf', it can be created from another resource this way: *xmlCreateFile(":ctf/new.xml", “newroot”)*.

If the file is in the current resource, only the file path is necessary, e.g. *xmlCreateFile(“new.xml”, “newroot”)*.

Note that if a different resource than default is being accessed, the caller resource needs access to general.ModifyOtherObjects in the [ACL](/docs/acl.md "wikilink").

-   **rootNodeName:** the name of the root node in the XML document.

### Returns

Returns the root [xmlnode](/docs/xmlnode.md "wikilink") object of the new XML file if successful, or *false* otherwise.

Example
-------

This example allows a player to use the command 'createfile' to create an .xml file.

``` lua
-- Creates a file named "new.xml" with root node "newroot" and childnode "newchild".
function createFileHandler()
local RootNode = xmlCreateFile("new.xml"," newroot")
local NewNode = xmlCreateChild(RootNode, "newchild")
xmlSaveFile(RootNode)
xmlUnloadFile(RootNode)
end

addCommandHandler("createfile", createFileHandler)
```

See Also
--------

[ru:xmlCreateFile](/docs/ru-xmlcreatefile.md "wikilink")
