getKeyBoundToFunction allows retrieval of the first key bound to a function.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
string getKeyBoundToFunction( player thePlayer, function theFunction )
```

### Required Arguments

-   **thePlayer:** The player you are checking the function bound to a key
-   **theFunction:** The function in which you would like to check the bound key

### Returns

Returns a string of the first key the function was bound to.

</section>
<section name="Client" class="client" show="true">
``` lua
string getKeyBoundToFunction( function theFunction )
```

### Required Arguments

-   **theFunction:** The function in which you would like to check the bound key

### Returns

Returns a string of the first key the function was bound to.

</section>
Example
-------

<section name="Client" class="client" show="true">
/key command gives bounded key to our chat function

``` lua
function chat ()
  outputChatBox("Test")
end
bindKey("F2","down",chat)

function key()
  local boundKey = getKeyBoundToFunction(chat)
  outputChatBox(boundKey)
end
addCommandHandler("key",key)
```

This example written by **Samurai**

</section>
See Also
--------
