This function returns whether the ingame chatbox is being used (accepting chatbox input) or not.

Syntax
------

``` lua
bool isChatBoxInputActive ()
```

### Returns

Returns *true* if the chatbox is receiving input, *false* if not active.

Example
-------

This example shows how you can check if a user has the chat box active (and presumably typing a message).

``` lua
if isChatBoxInputActive() then
    outputChatBox("You're typing")
end
```

See Also
--------
