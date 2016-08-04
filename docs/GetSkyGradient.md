This function will return the current sky color.

**Note:** The server can only return the sky color if it has actually been set by script.

Syntax
------

``` lua
int, int, int, int, int, int getSkyGradient ( )
```

### Returns

Returns 6 [ints](/int.md "wikilink"), of which the first 3 represent the sky's “top” color, (in RGB) and the last 3 represent the bottom colors.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function check()
    local r1, g1, b1, r2, g2, b2 = getSkyGradient()
    outputChatBox("Sky gradient colors are R: "..r1.." G: "..g1.." B: "..b1.." and R: "..r2.." G: "..g2.." B: "..b2)
end
addCommandHandler("skygradient", check)
```

</section>
See Also
--------
