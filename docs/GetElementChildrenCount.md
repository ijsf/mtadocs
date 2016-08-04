This function returns the number of children an element has. Note that only the direct children are counted and not elements that are further down the [element tree](/docs/element_tree.md "wikilink").

Syntax
------

``` lua
int getElementChildrenCount ( element parent )
```

### Required Arguments

-   **parent:** the parent element

### Returns

Returns an *int* with the number of child elements, or *false* if the parent element does not exist.

Example
-------

To get the number of children the 'team1' element has:

``` xml
<team1 id="red">
    <spawnpoint id="spawnpoint_0" posX="2507.8715820313" posY="2772.6071777344" posZ="10.8203125" rot="270" skin="285"/>
    <spawnpoint id="spawnpoint_1" posX="2508.060546875" posY="2780.3647460938" posZ="10.8203125" rot="270" skin="285"/>
    <spawnpoint id="spawnpoint_2" posX="2508.0053710938" posY="2776.2897949219" posZ="10.8203125" rot="270" skin="285"/>
    <spawnpoint id="spawnpoint_3" posX="2510.6899414063" posY="2778.3745117188" posZ="10.8203125" rot="270" skin="285"/>
</team1>
```

You could use the following code:

``` lua
local teamRed = getElementByID("red") -- find the parent element by its ID
local count = getElementChildrenCount (teamRed) -- get the total number of children
outputChatBox("Team red has " .. count .. " spawnpoints") -- output: Team red has 4 spawnpoints
```

Note that this does not only count spawnpoint elements, but all child elements. Thus if there would be child elements of other types, the message would be wrong and you'd have to loop through the children manually, checking the type of each.

See Also
--------
