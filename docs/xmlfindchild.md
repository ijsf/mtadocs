This function returns a named child node of an XML node.

Syntax
------

``` lua
xmlnode xmlFindChild ( xmlnode parent, string tagName, int index )
```

### Required Arguments

-   **parent**: This is an [xmlnode](/docs/xmlnode.md "wikilink") that you want to find the child node under.
-   **tagName**: This is the name of the child node you wish to find (case-sensitive).
-   **index**: This is the 0-based index of the node you wish to find. For example, to find the 5th subnode with a particular name, you would use 4 as the index value. To find the first occurence, use 0.

### Returns

Returns an [xmlnode](/docs/xmlnode.md "wikilink") if the node was found, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
If you wanted to find an *instructions* node in an xml file like this:

``` xml
<root version="2.0">
      <options>
            <instructions>Start at the beginning and keep going until the end!</instructions>
      </options>
</root>
```

You could use the following code to print the text in the *instructions* node to the chatbox:

``` lua
local rootNode = xmlLoadFile ( "test.xml" )
local optionsNode = xmlFindChild ( rootNode, "options", 0 )
local instructionsNode = xmlFindChild ( optionsNode, "instructions", 0 )
local instructions = xmlNodeGetValue ( instructionsNode )

outputChatBox ( instructions )
```

</section>
See Also
--------

[ru:xmlFindChild](/docs/ru:xmlFindChild.md "wikilink")
