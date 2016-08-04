This function allows you to disable the flying birds.

Syntax
------

``` lua
bool setBirdsEnabled ( bool enable )
```

### Required Arguments

-   **enabled:** A [boolean](/docs/boolean.md "wikilink") value determining if birds should be shown. Use *true* to show the birds and *false* to hide them.

### Returns

Returns *true* if the birds state was changed succesfully, *false* if an invalid argument was specified.

Example
-------

This example Enables or Disables the Birds.

<section name="Client" class="client" show="true">
``` lua
function setBirdsState()
    setBirdsEnabled(not getBirdsEnabled()) -- Disable the Birds if they're enabled, either Enable them.
    outputChatBox("The birds are now ".. (getBirdsEnabled() and "Enabled" or "Disabled") ..".") -- Output the new Birds state.
end
addCommandHandler("birds",setBirdsState) -- Add the command handler attached to the function "setBirdsState".
```

</section>
Requirements
------------

See Also
--------
