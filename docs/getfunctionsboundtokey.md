Gets the functions bound to a key. To bind a function to a key use the [bindKey](/docs/bindkey.md "wikilink") function

Syntax
------

<section name="Server" class="server" show="true" >
``` lua
table getFunctionsBoundToKey ( player thePlayer , string theKey )
```

### Required Arguments

-   **thePlayer:** The player to get the functions from a key.
-   **theKey:** The key you wish to check the functions from.

</section>
<section name="Client" class="client" show="true" >
``` lua
table getFunctionsBoundToKey ( string theKey )
```

### Required Arguments

-   **theKey:** The key you wish to check the functions from.

</section>
### Returns

Returns a table of the key function(s).

Example
-------

<section name="Client" class="client" show="true" >
This loops through all the keys and outputs the keyname and the function bound to that key.

``` lua

local keyTable = { "mouse1", "mouse2", "mouse3", "mouse4", "mouse5", "mouse_wheel_up", "mouse_wheel_down", "arrow_l", "arrow_u",
 "arrow_r", "arrow_d", "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k",
 "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "num_0", "num_1", "num_2", "num_3", "num_4", "num_5",
 "num_6", "num_7", "num_8", "num_9", "num_mul", "num_add", "num_sep", "num_sub", "num_div", "num_dec", "F1", "F2", "F3", "F4", "F5",
 "F6", "F7", "F8", "F9", "F10", "F11", "F12", "backspace", "tab", "lalt", "ralt", "enter", "space", "pgup", "pgdn", "end", "home",
 "insert", "delete", "lshift", "rshift", "lctrl", "rctrl", "[", "]", "pause", "capslock", "scroll", ";", ",", "-", ".", "/", "#", "\\", "=" }

addCommandHandler("gakf",function()
    for _,i in ipairs(keyTable)do --loop through keyTable
        for _,v in ipairs(getFunctionsBoundToKey(i))do --loop through the key bounded functions
            outputChatBox(i..":"..tostring(v)) --output the keyname and the function bound to it
        end
    end
end)
```

</section>
<section name="Server" class="server" >
This loops through all the keys and outputs the keyname and the function bound to that key.

``` lua
function output()
    outputChatBox("Hi")
end
bindKey(root,"f2","down",output)
local keyTable = { "mouse1", "mouse2", "mouse3", "mouse4", "mouse5", "mouse_wheel_up", "mouse_wheel_down", "arrow_l", "arrow_u",
 "arrow_r", "arrow_d", "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k",
 "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "num_0", "num_1", "num_2", "num_3", "num_4", "num_5",
 "num_6", "num_7", "num_8", "num_9", "num_mul", "num_add", "num_sep", "num_sub", "num_div", "num_dec", "F1", "F2", "F3", "F4", "F5",
 "F6", "F7", "F8", "F9", "F10", "F11", "F12", "backspace", "tab", "lalt", "ralt", "enter", "space", "pgup", "pgdn", "end", "home",
 "insert", "delete", "lshift", "rshift", "lctrl", "rctrl", "[", "]", "pause", "capslock", "scroll", ";", ",", "-", ".", "/", "#", "\\", "=" }

addCommandHandler("gakf",function(source) --source is the player
    for _,i in ipairs(keyTable)do --loop through keyTable
        for _,v in ipairs(getFunctionsBoundToKey(source,i))do --loop through the key bounded functions
            outputChatBox(i..":"..v,source) --output the keyname and the function bound to it
        end
    end
end)
```

</section>
See Also
--------
