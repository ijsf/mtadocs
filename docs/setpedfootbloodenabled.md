This function makes a players foot prints bloody.

Syntax
------

``` lua
bool setPedFootBloodEnabled (element thePlayer, bool enabled)
```

### Required Arguments

-   **thePlayer:** The player to give bloody foot prints to.
-   **enabled:** Boolean specifying whether or not to have bloody feet.

### Returns

Returns *true* if changing the players bloody feet status worked.

Example
-------

This example gives the player bloody feet forever.

<section name="Client" class="client" show="true">
``` lua
setPedFootBloodEnabled(localPlayer, true)
```

</section>
See Also
--------
