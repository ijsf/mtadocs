This function is used to retrieve a list of the child elements of a given parent element. Note that it will only return direct children and not elements that are further down the [element tree](/docs/element_tree.md "wikilink").

Syntax
------

``` lua
table getElementChildren ( element parent [, string theType = nil ] ) 
```

### Required Arguments

-   **parent:** Supply this argument with the parent of the children you want returned.

### Optional Arguments

-   **theType:** The type of element you want a list of. This is the same as the tag name in the .map file, so this can be used with a custom element type if desired. Built in types are:
    -   **“player”:** A player connected to the server
    -   **“ped”:** A ped
    -   **“water”:** A water polygon
    -   **“sound”:** A playing sound
    -   **“vehicle”:** A vehicle
    -   **“object”:** An object
    -   **“pickup”:** A pickup
    -   **“marker”:** A marker
    -   **“colshape”:** A collision shape
    -   **“blip”:** A blip
    -   **“radararea”:** A radar area
    -   **“team”:** A team
    -   **“spawnpoint”:** A spawnpoint
    -   **“remoteclient”:** A remote client connected to the server
    -   **“console”:** The server Console

### Returns

This function returns a *table* that contains a list of elements that the parent has. If the element has no children, it will return an empy *table*. It will return *false* if the parent element does not exist.

Example
-------

With this map file:

``` xml
<team1 id="red">
    <base name="Mountain Top" />
    <base name="Docks" />
    <base name="Airport" />
    <anything name="no base" />
</team1>
```

This example outputs the child elements of the element with id 'red', when the player enters the 'teamElements' command.

``` lua
function showTeamElements(thePlayer, command)
    local theTeam = getElementByID("red")         -- get the team element
    local elements = getElementChildren(theTeam)  -- the child elements
    for k,v in ipairs(elements) do
        outputChatBox(getElementType(v)..": "..getElementData(v, "name")) -- print the type and name of each child
    end
end
addCommandHandler("teamElements", showTeamElements)
```

At a later point you could loop through all the elements and process their contents any way you wish. Remember to make sure you only have the *current* list of elements though. If you get the root element children, then wait a while for things to change, this list won't be up to date unless you use [getElementChildren](/docs/getElementChildren.md "wikilink") again.

See Also
--------
