<lowercasetitle></lowercasetitle>

This function is used to remove hex color codes from strings.

Syntax
------

``` lua
string removeHex (string text)
```

### Required Arguments

-   **text**: The text from which you want to remove the hex codes.

### Returns

Returns the modified string if the conversion was successful, false otherwise.

Code
----

<section name="Code" class="both" show="true">
``` lua
function removeHex (text)
    return type(text)=="string" and string.gsub(text, "#%x%x%x%x%x%x", "") or text
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example remove color coding from player nickname when he join the server.

``` lua
function nickname()
   local name = getPlayerName(source)
   local new = removeHex (name)
   if (new ~= name) then
      setPlayerName(source, new)
   end
end
addEventHandler("onPlayerJoin", root, nickname)
```

</section>
Author: Walid

See Also
--------
