This function is used to show or hide a [player](/player.md "wikilink")'s cursor.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool showCursor ( player thePlayer, bool show, [ bool toggleControls = true ] )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") you want to show or hide the cursor of.
-   **show:** A boolean value determining whether to show (*true*) or hide (*false*) the cursor.

### Optional Arguments

-   **toggleControls:** A boolean value determining whether to disable controls whilst the cursor is showing. *true* implies controls are disabled, *false* implies controls remain enabled.

</section>
<section name="Client" class="client" show="true">
``` lua
bool showCursor ( bool show, [ bool toggleControls = true ]  )
```

### Required Arguments

-   **show:** A boolean value determining whether to show (*true*) or hide (*false*) the cursor.

### Optional Arguments

-   **toggleControls:** A boolean value determining whether to disable controls whilst the cursor is showing. *true* implies controls are disabled, *false* implies controls remain enabled.

</section>
### Returns

Returns *true* if the player's cursor was shown or hidden successfully, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example shows the cursor for a player named “Dave”, then outputs a message if it was shown successfully.

``` lua
local thePlayer = getPlayerFromName ( "Dave" )              -- get the player named Dave
if thePlayer then                                           -- if we got him
    showCursor ( thePlayer, true )                          -- make his cursor show
    if isCursorShowing ( thePlayer ) then                   -- did it show?
        outputChatBox ( "Cursor is now showing for Dave." ) -- print a message to the chat box
    end
end
```

</section>
<section name="Client" class="client" show="true">
This example shows the cursor all the time

``` lua
showCursor ( true ) -- Shows cursor
showCursor ( false ) -- Doesnt Show Cursor
```

</section>
See Also
--------
