This function is used to determine the parent of an *element*.

Syntax
------

``` lua
element getElementParent ( element theElement )  
```

### Required Arguments

-   **theElement:** The child of the parent element you want returned.

### Returns

This returns the parent as an *element*. It returns *false* if *theElement* is invalid, or is the root node.

Example
-------

<section name="Server" class="server" show="true">
Consider the following map file:

``` xml
<spawngroup id="red">
   <spawnpoint id="spawnpoint_0" posX="2507.8715820313" posY="2772.6071777344" posZ="10.8203125" rot="270" skin="285"/>
   <spawnpoint id="spawnpoint_1" posX="2508.060546875" posY="2780.3647460938" posZ="10.8203125" rot="270" skin="285"/>
</spawngroup>
<spawngroup id="blue">
   <spawnpoint id="spawnpoint_5" posX="2733.4184570313" posY="2753.1276855469" posZ="10.8203125" rot="90" skin="124"/>
   <spawnpoint id="spawnpoint_6" posX="2733.5258789063" posY="2748.1110839844" posZ="10.8203125" rot="90" skin="125"/>
</spawngroup>
```

This function determines a spawnpoint's parent element, and announces its ID:

``` lua
function spawnpointUse ( thePlayer )             -- this function gets called whenever a spawnpoint is used
   theSpawnGroup = getElementParent ( source )   -- get the spawnpoint's parent element
   -- announce the parent's ID and the player who spawned there:
   outputChatBox ( getPlayerName ( thePlayer ) .. " spawned at team " .. getElementID ( theSpawnGroup ) .. "'s spawnpoint." )
   -- Example output: "Joe spawned at team blue's spawnpoint."
end
addEventHandler ( "onSpawnpointUse", root, spawnpointUse )
```

</section>
See Also
--------
