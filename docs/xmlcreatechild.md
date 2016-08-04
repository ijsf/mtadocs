This function creates a new child node under an XML node.

Syntax
------

``` lua
xmlnode xmlCreateChild ( xmlnode parentNode, string tagName )
```

### Required Arguments

-   **parentNode:** the [xmlnode](/docs/xmlnode.md "wikilink") you want to create a new child node under.
-   **tagName:** the type of the child node that will be created.

### Returns

Returns the created [xmlnode](/docs/xmlnode.md "wikilink") if successful, *false* otherwise.

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

[ru:xmlCreateChild](/docs/ru:xmlcreatechild.md "wikilink")
