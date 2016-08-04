[frame|Element tree](/File:Tre.png.md "wikilink") MTA uses a so-called *element tree* to store all the elements that exist on the server and the client. This is directly related to the set of running [resources](/resources.md "wikilink") and their map files' XML layout, although it can be changed at run-time by scripts.

If you are familiar with the concept of *trees* in computer-science, this should be easy to understand. If you are not, think of it like a family tree - except everyone only has a single parent. Every [element](/element.md "wikilink") has a *parent* element.

All elements that are created within scripts or from .map files are child elements of the resource they belong to. Thus, most elements (except for [clients](/client.md "wikilink")) exist only within resources and are also destroyed as soon as their resource is stopped.

Tree elements
-------------

-   **root**: This is at the very base of the tree - all elements are children (or descendants) of this element.

``` lua
getRootElement()
```

-   **resource**: These are direct children of the root element - with one for each *running* resource. This element is called the *resource root*. Its ID holds the name of the resource.

``` lua
getResourceRootElement()
```

-   **map**: Each resource element contains at least one map element, representing either a ".map" file in the resource or the one containing the elements created by scripts (this is called the *dynamic* map). Their IDs contain the maps' filenames, or *dynamic* for the dynamic map.
    -   Map files can contain a number of other [elements](/element.md "wikilink") as well as an unlimited number of custom elements.

Example
-------

This in an example of a serverside tree dumped to XML from a running server. *Please note that it is shortened on some places for the sake of overview.*

``` xml
<root>
    <console/>
    <player dontRespawn="false"/>
    <player dontRespawn="false" lastSpawnarea=""/>
    <resource id="resourcebrowser"/>
    <resource id="ajax"/>
    <resource id="resourcemanager"/>
    <resource id="spawnmanager"/>
    <resource id="mapmanager"/>
    <resource id="runcode"/>
    <resource id="fr">
        <map id="dynamic">
            <vehicle/>
        </map>
    </resource>
    <resource id="elementbrowser"/>
    <resource id="assault">
        <map id="dynamic">
            <team/>
            <team/>
            <blip/>
            <marker/>
            <colshape/>
            <blip/>
            <blip/>
        </map>
    </resource>
    <resource id="as-farm">
        <map id="dynamic"/>
        <map id="as-farm.map">
            <spawngroup req="" type="attacker">
                <spawnarea posY="-8.3976354598999" posX="20.182683944702" skins="9" ... />
            </spawngroup>
            <spawngroup req="" type="attacker">
                <spawnarea posY="32.166355133057" posX="-46.90763092041" skins="9" ... />
            </spawngroup>
            <spawngroup req="" type="attacker">
                <spawnarea posY="35.214984893799" posX="-33.486911773682" skins="9" ... />
            </spawngroup>
            <spawngroup req="" type="attacker">
                <spawnarea posY="35.214984893799" posX="-33.486911773682" skins="9" ... />
            </spawngroup>
            <objective id="first" type="checkpoint" description="Breach into the farm" ... />
            <pickup type="weapon" ... />
        </map>
    </resource>
</root>
```

### Explanation

This tree consists of a number of resource root elements, the [server console](/Element/Console.md "wikilink") and two [player](/player.md "wikilink") elements, that are direct children of the **root** element. All these resources have a *dynamic map* as child element (it is just not shown for most of them). These contain the elements that are created dynamically by this resource using scripts, for example a [vehicle](/vehicle.md "wikilink"). If the resource has a map file, it is also a child element, itself containing all the elements in the .map file.

Let's have a closer look at the **assault** resource: This contains just one *dynamic* map that has 2 teams, 3 blips, 1 marker and 1 colshape as child elements. These are the elements that are created by the script, for example the marker, the colshape and one of the blips are probably used for the objective.

The **as-farm** resource's function on the contrary is to be a map for the **assault** gamemode. The dynamic map is empty (it could contain elements if there was a script in it though), while there is a map called 'as-farm.map', that contains a number of elements. These are mostly custom elements (like spawngroup, spawnarea, objective) but also a few elements that MTA creates automactically after loading the map (like pickup). In the brackets after the element type, you can see the element data it contains. These are identical with the attributes the .map file contains within these elements, while you can also set and get element data for any other elements (e.g. players) with [setElementData](/setElementData.md "wikilink") and [getElementData](/getElementData.md "wikilink").

Pratical application
--------------------

Elements can have as many children as they like. This does not directly affect the map in any way, but it comes in to its own when combined with the scripting system.

### Setting data for elements

If you call a set... function on a node of the element tree, the function will affect every element within it (that it can work on).

So, the following code would set the size of every marker (the only type of element the setMarkerSize function can work on) that is below the root element to *2.5*.

``` lua
setMarkerSize ( getRootElement(), 2.5 )
```

The same can be done on any element, it is not restricted to the root element.

### Map manager

The [example above](/#Example.md "wikilink") shows the way the [map manager](/map_manager.md "wikilink") uses different resources. The 'assault' resource is the gamemode, that manages what happens on the server using scripts and thus by creating elements in the tree dynamically. When a map resource is started, the gamemode receives a [resource pointer](/resource.md "wikilink") referring to the started resource - in this case *as-farm* - from which you can retrieve and store the resource root element. Using this element in conjunction with functions like [getElementsByType](/getElementsByType.md "wikilink"), [getElementData](/getElementData.md "wikilink") and various others, you can access any of the information that was loaded into the tree from the 'as-farm.map'-file through scripts in the gamemode resource.

Another thing that has to be considered related to the tree of elements is the fact that when you change the map, you don't have to remove any elements you created within the map resource, while you **do** have to remove elements that are created within the gamemode resource, **if** they are specific to the map (which will be probably the case for those items you create based on information read from the map resource's .map files).

Element browser
---------------

You can start the resource *elementbrowser* to see a live view of the element tree on your server. Just start the resource and browser to your server's web page and choose the *Element browser* option in the sidebar (firefox only currently). [Category:Scripting Concepts](/Category:Scripting_Concepts.md "wikilink") [es:Árbol de elementos](/es:Árbol_de_elementos.md "wikilink") [ru:Element tree](/ru:Element_tree.md "wikilink")
