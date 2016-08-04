This function is used for setting an element as the parent of another element.

Syntax
------

``` lua
bool setElementParent ( element theElement, element parent )  
```

### Required Arguments

-   **theElement:** The element that you wish to set the parent of.
-   **parent:** The element you wish to be the parent of *theElement*.

### Returns

Returns *true* if both [elements](/docs/element.md "wikilink") are valid, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example sets the parent of each spawnpoint to a dummy element:

``` lua
dummyElem = createElement ( "spawngroup", "Group of spawn points" ) -- create a dummy element
local spawnpoints = getElementsByType ( "spawnpoint" ) -- get a table of spawn point elements
for k,v in ipairs (spawnpoints) do -- loop through the table of spawn points
   setElementParent ( v, dummyElem ) -- set the dummy element as the parent of the spawn point
end
-- all of the spawn points are now children of 'dummyElem'
```

This is the equivalent of:

``` xml
<spawngroup id="Group of spawn points">
   <spawnpoint id="spawnpoint_0" posX="2507.8715820313" posY="2772.6071777344" posZ="10.8203125" rot="270" skin="285"/>
   <spawnpoint id="spawnpoint_1" posX="2508.060546875" posY="2780.3647460938" posZ="10.8203125" rot="270" skin="285"/>
   <spawnpoint id="spawnpoint_2" posX="2508.0053710938" posY="2776.2897949219" posZ="10.8203125" rot="270" skin="285"/>
   <spawnpoint id="spawnpoint_3" posX="2510.6899414063" posY="2778.3745117188" posZ="10.8203125" rot="270" skin="285"/>
</spawngroup>
```

</section>
See Also
--------
