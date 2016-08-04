This function destroys a XML node from the XML node tree.

Syntax
------

``` lua
bool xmlDestroyNode ( xmlnode theXMLNode )
```

### Required Arguments

-   **theXMLNode:** The [xml node](/xml_node.md "wikilink") you want to destroy.

### Returns

Returns *true* if the [xml node](/xml_node.md "wikilink") was successfully destroyed, *false* otherwise.

### Example

<section name="Server" class="server" show="true">
This example will add a command called '/delnode' and it will create an xml file called 'test.xml'.

``` lua
addEventHandler("onResourceStart", resourceRoot, function()
    xml = xmlLoadFile("test.xml")
    if not xml then
        xml = xmlCreateFile("test.xml", "root")
        xmlCreateChild(xml, "node")
        xmlSaveFile(xml)
    end
end)

addCommandHandler("delnode", function(player)
    local node = xmlFindChild(xml, "node", 0)
    if not node then xmlUnloadFile(xml) return end
    xmlDestroyNode(node)
    xmlSaveFile(xml)
    xmlUnloadFile(xml)
    outputChatBox("You destroyed the node!", player, 0, 255, 0, false)
end)
```

</section>
See Also
--------

[ru:xmlDestroyNode](/ru:xmlDestroyNode.md "wikilink")
