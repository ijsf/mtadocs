Sets player's level if the player is currently in a gang.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setPlayerLevel ( player Player, integer Level )
```

Required Arguments
------------------

-   **Player:** Player whose level you want to change
-   **Level:** Integer of the level you want to set as player's level from 1 to 5

</section>
<section name="Client" class="client" show="true">
``` lua
bool setPlayerLevel ( player Player, integer Level )
```

Required Arguments
------------------

-   **Player:** Player whose level you want to change
-   **Level:** Integer of the level you want to set as player's level from 1 to 5

</section>
Returns
-------

-   **Success:** Boolean that is true if the level was changed successfully or false otherwise
