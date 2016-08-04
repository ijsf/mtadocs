This outputs the specified text string to the console window (accessed with F8 or ~ key). It can be specified as a message to certain player(s) or all players.

Syntax
------

<section name="Client" class="client" show="true">
``` lua
bool outputConsole ( string text )
```

### Required Arguments

-   **text:** The text string that you wish to send to the console window

</section>
<section name="Server" class="server" show="true">
``` lua
 )
```

### Required Arguments

-   **text:** The text string that you wish to send to the console window

### Optional Arguments

-   **visibleTo:** This specifies who the chat is visible to. Any players in this element will see the chat message. See [visibility](/visibility.md "wikilink").

</section>
Example
-------

<section name="Server" class="server" show="true">
This code creates two console commands. One, 'public', will post a message in the consoles of all players, and the other, 'private', will post a message in only the console of the player that executed the command.

``` lua
function message(player,command)
    if command == "public" then
        outputConsole("Public console message")
    else
        outputConsole("Private console message",player)
    end
end
addCommandHandler("public",message)
addCommandHandler("private",message)
```

</section>
See Also
--------
