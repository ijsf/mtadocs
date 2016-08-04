This function is used to show or hide the player's chat.

Syntax
------

<section name="Client" class="client" show="true">
``` lua
bool showChat ( bool show )
```

### Required Arguments

-   **show:** A boolean value determining whether to show (*true*) or hide (*false*) the chat.

### Returns

Returns *true* if the player's chat was shown or hidden successfully, *false* otherwise.

</section>
<section name="Server" class="server" show="true">
``` lua
bool showChat ( player thePlayer, bool show )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") whose chat is to be hidden or shown.
-   **show:** A boolean value determining whether to show (*true*) or hide (*false*) the chat.

### Returns

Returns *true* if the player's chat was shown or hidden successfully, *false* otherwise.

</section>
Example
-------

<section name="Client" class="client" show="true">
This example toggle's the player's chat when they press the "**i**" key.

``` lua
--This example below is for all versions until 1.4:
local isChatVisible = true --Let's assume the chat is visible as soon as the resource starts.

function chat(key, keyState)
    if isChatVisible then --Check or the chat is visible.
        showChat(false) --If it is, hide it.
        isChatVisible = false
    else
        showChat(true) --If it is not, show it.
        isChatVisible = true
    end
end

bindKey("i", "down", chat) --Make a bind key to start the function as soon as a player presses the key 'i'


--This example below is for version 1.4 and up:
function chat(key, keyState)
    if isChatVisible() then --Check or the chat is visible.
        showChat(false) --If it is, hide it.
    else
        showChat(true) --If it is not, show it.
    end
end

bindKey("i", "down", chat) --Make a bind key to start the function as soon as a player presses the key 'i'
```

</section>
See Also
--------
