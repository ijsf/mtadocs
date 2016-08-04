This function will tell you if the birds are enabled or disabled.

Syntax
------

``` lua
bool getBirdsEnabled ()
```

### Returns

Returns *true* if the birds are enabled or *false* if the birds are disabled.

Example
-------

This example outputs the Birds state.

<section name="Client" class="client" show="true">
``` lua
function areBirdsEnabled()
    outputChatBox("The birds are currently ".. (getBirdsEnabled() and "Enabled" or "Disabled") ..".") -- Output the birds state.
end
addCommandHandler("birds", areBirdsEnabled) -- Add the command handler attached to the function "areBirdsEnabled".
```

</section>
Requirements
------------

See Also
--------
