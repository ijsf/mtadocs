This function returns a named sub node of a particular XML node.

Syntax
------

``` lua
xmlnode xmlFindSubNode ( xmlnode parent, string subnode, int index )
```

### Required Arguments

-   **parent**: This is an [xmlnode](/docs/xmlnode.md "wikilink") that you want to find the subnode under. This could be a node returned from another call to [xmlFindSubNode](/docs/xmlfindsubnode.md "wikilink").
-   **subnode**: This is the name of the subnode you wish to find.
-   **index**: This is the index of the node you wish to find. For example, to find the 5th subnode with a particular name, you would use 4 as the index value. To find the first occurence, use 0.

### Returns

Returns an [xmlnode](/docs/xmlnode.md "wikilink") object if the node was found, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
If you wanted to find the 'instructions' node in a map file like this:

``` xml
<map version="2.0">
      <options>
            <instructions>Start at the begining and keep going until the end!</instructions>
      </options>
</map>
```

You could use the following code:

``` lua
maproot = getLoadedMapXMLRoot ()
optionsnode = xmlFindSubNode ( maproot, "options", 0 )
instructionsnode = xmlFindSubNode ( optionsnode, "instructions", 0 )
```

</section>
See Also
--------
