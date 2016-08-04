This function saves a loaded XML file.

Syntax
------

``` lua
bool xmlSaveFile ( xmlnode rootNode ) 
```

### Required Arguments

-   **rootNode:** the root [xmlnode](/xmlnode.md "wikilink") of the loaded XML file.

### Returns

Returns *true* if save was successful, *false* if the XML file does not exist.

Example
-------

<section name="Client" class="client" show="true">
This example allows a player to use the command 'createfile' to create an .xml file.

``` lua
-- Creates a file named "new.xml" with root node "newroot" and childnode "newchild".
function createFileHandler()
local RootNode = xmlCreateFile("new.xml"," newroot")
local NewNode = xmlCreateChild(RootNode, "newchild")
xmlSaveFile(RootNode)
end

addCommandHandler("createfile", createFileHandler)
```

</section>
See Also
--------

[ru:xmlSaveFile](/ru:xmlSaveFile.md "wikilink")
