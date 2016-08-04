This function returns a string containing the name of the specified player.

Syntax
------

``` lua
string getPlayerName ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** the Player that you want to get his name

### Returns

Returns a string containing the requested player's name, or *false* if the player passed to the function is invalid.

### Limits

-   Player name can consist of ASCII characters between 33 and 126 are allowed (basic latin):

``    !"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijklmnopqrstuvwxyz{|}~ ``

-   Minimal player name length is 1 character.
-   Maximum player name length is 22 characters.
-   Player names are case-insensitive. It is not possible to have two clients with same name but different character case.

Example
-------

<section name="Server" class="server" show="true">
``` lua
addCommandHandler("myname",
  function(playerSource)
    outputChatBox("Your name: "..getPlayerName(playerSource), playerSource)
  end
)
```

</section>
<section name="Client" class="client" show="true">
This example outputs the local player name to the chatbox.

``` lua
addCommandHandler("myname",
  function()
   local localPlayerName = getPlayerName(getLocalPlayer())
   --and we output it to the chatbox
   outputChatBox(localPlayerName)
  end
)
```

</section>
See Also
--------
