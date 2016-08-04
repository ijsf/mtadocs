This function is used to edit an attribute of a node in a configuration file.

Syntax
------

``` lua
bool xmlNodeSetAttribute ( xmlnode node, string name, string/float value )             
```

### Required Arguments

-   **node:** The node of which you wish to edit an attribute.
-   **name:** The name of the attribute.
-   **value:** The value which you wish to change the attribute to. (**Note:** *nil* will delete the attribute)

### Returns

Returns *true* if the attribute was set successfully, *false* if the node and/or attribute do not exist, or if they're faulty.

Example
-------

<section name="Server" class="server" show="true">
In a gamemode, we want a command to change the marker color in the configuration file and remove a deprecated attribute.

config.xml:

``` xml
<config>
    <markers color="255,100,0" foo="deprecated" />
</config>
```

Lua code:

``` lua

function changeConfigMarkerColor(thePlayer, command, r, g, b)
    local config = xmlLoadFile("config.xml")
    local markernode = xmlFindChild(config, "markers", 0)
    xmlNodeSetAttribute(markernode, "color", r .. "," .. g .. "," .. b)
    xmlNodeSetAttribute(markernode, "foo", nil) -- remove 'foo' attribute
    xmlSaveFile(config)
    xmlUnloadFile(config)
end
addCommandHandler("markercolor", changeConfigMarkerColor)
```

</section>
See Also
--------

[ru:xmlNodeSetAttribute](/docs/ru:xmlnodesetattribute.md "wikilink")
