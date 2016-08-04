<lowercasetitle></lowercasetitle>

This function generates a random HEX color code.

Syntax
------

``` lua
string, string generateRandomHEXColor()
```

### Returns

Returns two strings, the first contains the '\#', the second doesn't.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function generateRandomHEXColor()
    local randomColor = string.sub(md5(tostring(math.random())),1,6)
    return "#" .. randomColor, randomColor
end
```

</section>
Example
-------

<section name="Example" class="server" show="true">
This example outputs a text to the chatbox with a random color, and tell the players the color code.

``` lua
function outputRandomColor()
    withHash,withoutHash = generateRandomHEXColor()
    outputChatBox(withHash .. "This is a random color. [" .. withoutHash .. "]", root, 255, 255, 255, true)
end

addCommandHandler("randomcolor", outputRandomColor)
```

</section>
Function created by **Norbert Kovács \# Gr0x**.

See Also
--------
