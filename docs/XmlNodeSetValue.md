This function is made to be able to assign values to tags in XML files (eg. <something>anything</something>).

Syntax
------

``` lua
bool xmlNodeSetValue ( xmlnode theXMLNode, string value [, bool setCDATA = false] )            
```

### Required Arguments

-   **theXMLNode:** The [xml node](/xml_node.md "wikilink") you want to set the value of.
-   **value:** The [string](/string.md "wikilink") value you want the node to have.

### Returns

Returns *true* if value was successfully set, *false* otherwise.

Example
-------

<section name="Server Example" class="server" show="false">
In this example a sample value is inserted into a XML file.

``` lua
local xmlFile = xmlLoadFile ( "exampleFile.xml" ) -- Open a file already created
if xmlFile then -- If it's indeed opened
    local node = xmlCreateChild ( xmlFile, "somesubnode" ) -- Create a new subnode
    local success = xmlNodeSetValue ( node, "somevalue" ) -- Set the value of it
    if success then -- Check if it was successful
        xmlSaveFile ( xmlFile ) -- Save the file
    end
end
```

After both changing the value and saving the XML file with [xmlSaveFile](/xmlSaveFile.md "wikilink"), the file will look like this:

<section name="exampleFile.xml" class="server" show="true">
``` xml
<somenode>
    <somesubnode>somevalue</somesubnode>
</somenode>
```

</section>
<section name="Client Example: Save and load from a clientside XML" class="client" show="true">
This shows an example of a clientside XML file. You can use this to store user preferences and load them the next time the script loads. Almost always, you should have an options GUI for clients to interact with to set these values.
Since the XML will change, it should NOT be included in the resource's meta.xml file. MTA will think that file is corrupted and will download it again from the server. Instead, you should create the XML within the script, and then load it within the script on future script runs if it exists.

**This xml will be created from the script following it below**

``` xml
<root>
    <hud_display>
        <IconSizeX>60</IconSizeX>
        <IconSizeY>60</IconSizeY>
    </hud_display>
    <hud_binds>
        <weaponSlot0>tab</weaponSlot0>
        <weaponSlot1>1</weaponSlot1>
    </hud_binds>
</root>
```

**This script will create the xml or load it if it exists**

``` lua
function ClientResourceStart ()
    xmlRootTree = xmlLoadFile ( "userSettings.xml" ) --Attempt to load the xml file 

    if xmlRootTree then -- If the xml loaded then...
        xmlHudBranch = xmlFindChild(xmlRootTree,"hud_display",0) -- Find the hud sub-node
        xmlBindsBranch = xmlFindChild(xmlRootTree,"hud_binds",0) -- Find the binds sub-node
        outputChatBox ( "XML Found and Loaded" )
    else -- If the xml does not exist then...
        xmlRootTree = xmlCreateFile ( "userSettings.xml", "root" ) -- Create the xml file   
        xmlHudBranch = xmlCreateChild ( xmlRootTree, "hud_display" ) -- Create the hud sub-node under the root node
        xmlBindsBranch = xmlCreateChild ( xmlRootTree, "hud_binds" )-- Create the binds sub-node under the root node
        xmlNodeSetValue (xmlCreateChild ( xmlHudBranch, "IconSizeX"), "60" ) --Create sub-node values under the hud sub-node
        xmlNodeSetValue (xmlCreateChild ( xmlHudBranch, "IconSizeY"), "60" ) --Create sub-node values under the hud sub-node
        xmlNodeSetValue (xmlCreateChild ( xmlBindsBranch, "weaponSlot0"), "tab" ) --Create sub-node values under the binds sub-node
        xmlNodeSetValue (xmlCreateChild ( xmlBindsBranch, "weaponSlot1"), "1" ) --Create sub-node values under the binds sub-node
        outputChatBox ( "XML Created" )
    end

    --Retrieve a single sub-node name or value
    outputChatBox( "Node name: "..xmlNodeGetName (xmlFindChild(xmlHudBranch,"IconSizeX",0)), 0, 0, 255 ) --blue outputs
    outputChatBox( "Node Value: "..xmlNodeGetValue (xmlFindChild(xmlHudBranch,"IconSizeX",0)), 0, 0, 255 ) --blue outputs
    
        --Retrieve multiple sub-node names or values    
    xmlHudChildrenTable = xmlNodeGetChildren ( xmlHudBranch ) --Create a table of this branch's children
    for i,node in pairs(xmlHudChildrenTable ) do --Loop through the branch's children for sub-nodes
            outputChatBox( "Node name: "..xmlNodeGetName (node), 0, 255, 0 ) --green outputs
        outputChatBox( "Node Value: "..xmlNodeGetValue(node), 0, 255, 0 ) --green outputs
    end
end
addEventHandler ( "onClientResourceStart", resourceRoot, ClientResourceStart )
 
function ClientResourceStop ()
    xmlSaveFile ( xmlRootTree ) --Save the xml from memory for use next time
    xmlUnloadFile ( xmlRootTree ) --Unload the xml from memory
    outputChatBox ( "Saved and unloaded the XML." )
end
addEventHandler ( "onClientResourceStop", resourceRoot, ClientResourceStop )
```

</section>
See Also
--------
