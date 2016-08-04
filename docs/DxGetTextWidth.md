This function retrieves the theoretical width of a certain piece of text, if it were to be drawn using [dxDrawText](/docs/dxDrawText.md "wikilink").

**NOTE:** This function is relative to the client's screen resolution.

Syntax
------

``` lua
float dxGetTextWidth ( string text, [float scale=1, mixed font="default", bool bColorCoded=false] )
```

### Required Arguments

-   **text:** A string representing the text for which you wish to retrieve with width for.

Optional Arguments
------------------

-   **scale:** The size of the text.
-   **font:** Either a custom [DX font](/docs/DX_font.md "wikilink") element or the name of a built-in dx font:

-   **bColorCoded:** Should we exclude color codes from the width? (false will include the hex in the length)

### Returns

Returns the float of the width of the text.

Example
-------

<section name="Example" class="client" show="true">
This will show you the width of a message in a normal chatbox sent by a player

``` lua
function dxwidth(msg)
    chatbox = getChatboxLayout()
    local length = dxGetTextWidth(msg,chatbox["chat_scale"][1])
    outputChatBox(tostring(length))
end
addEventHandler("onClientChatMessage",root,dxwidth)
```

</section>
See Also
--------
