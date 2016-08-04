This function allows you to set the [interior](/docs/interior.md "wikilink") of any element. An interior is the current loaded place, 0 being outside.

Syntax
------

``` lua
bool setElementInterior ( element theElement, int interior [, float x, float y, float z] )
```

### Required Arguments

-   **theElement:** The element in which you'd like to set the interior of.
-   **interior:** The interior you want to set the element to. Valid values are 0 to 255.

### Optional Arguments

-   **x:** A floating point number representing the X coordinate on the map.
-   **y:** A floating point number representing the Y coordinate on the map.
-   **z:** A floating point number representing the Z coordinate on the map.

### Returns

Returns *true* if **theElement** and **interior** are valid arguments, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
In this example, if a player were to type /interior 1, they would be teleported into this interior

``` lua
function interior ( source, commandName, interior )
  --Let's see if they gave an interior ID
  if ( interior ) then
    --They did, so lets assign them to that interior and teleport them there (all in 1 function call!)
    setElementInterior ( source, interior, 2233.91, 1714.73, 1011.38 )
  else
    --They didn't give one, so set them to the interior they wanted, but don't teleport them.
    setElementInterior ( source, 0 )
  end
end
addCommandHandler ( "interior", interior )
```

</section>
<section name="Client" class="client" show="true">
In this example, if a player were to type /interior 1, they would be teleported into this interior

``` lua
function interior ( commandName, interior )
  --Let's see if they gave a interior ID
  if ( interior ) then
    --They did, so let's assign them to that interior and teleport them there (all in 1 function call!)
    setElementInterior ( localPlayer, interior, 2233.91, 1714.73, 1011.38 )
  else
    --They didn't give one, so set them to the interior they wanted, but don't teleport them.
    setElementInterior ( localPlayer, 0 )
  end
end
addCommandHandler ( "interior", interior )
```

</section>
See Also
--------

[de:setElementInterior](/docs/de:setelementinterior.md "wikilink")
