Unloads an XML document from memory.

Syntax
------

``` lua
bool xmlUnloadFile ( xmlnode node )               
```

### Required Arguments

-   **node:** root of the XML document to unload

### Returns

Returns *true* if the document was unloaded successfully, *false* otherwise.

Example
-------

Modify a configuration file.

config.xml:

``` xml
<config>
    <markers color="255,100,0" />
</config>
```

Lua code:

``` lua
xml = xmlLoadFile("config.xml")
markernode = xmlFindChild(xml, "markers", 0)
xmlNodeSetAttribute(markernode, "color", "0,0,200")
xmlSaveFile(xml)
xmlUnloadFile(xml)
```

See Also
--------

[ru:xmlUnloadFile](/docs/ru-xmlunloadfile.md "wikilink")
