Binds a player's key to a handler function or command, which will be called when the key is pressed.

Syntax
------

<section name="Server - Syntax 1" class="server" show="true">
``` lua
 )
```

### Required Arguments

-   **thePlayer:** The player you wish to bind the key of.
-   **key:** The key or control you wish to bind to the command. See [key names](/docs/key_names.md "wikilink") for a list of possible keys and [control names](/control_names.md "wikilink") for a list of possible controls.
-   **keyState:** A string that has one of the following values:
    -   **“up”:** If the bound key should trigger the function when the key is released
    -   **“down”:** If the bound key should trigger the function when the key is pressed
    -   **“both”:** If the bound key should trigger the function when the key is pressed or released
-   **handlerFunction:** The function that will be triggered when the player's key is pressed. This function should have the form:

  
``` lua
 )
```

The values passed to this function are:

-   **keyPresser:** The player who pressed the key
-   **key:** The key that was pressed
-   **keyState:** The state of the key that was pressed, *down* if it was pressed, *up* if it was released.
-   **arguments** The optional arguments you specified when calling [bindKey](/docs/bindKey.md "wikilink") (see below).

</section>
<section name="Client - Syntax 1" class="client" show="true">
``` lua
 ) 
```

### Required Arguments

-   **key:** The key or control you wish to bind to the command. See [key names](/docs/key_names.md "wikilink") for a list of possible keys and [control names](/control_names.md "wikilink") for a list of possible controls.
-   **keyState:** A string that has one of the following values:
    -   **“up”:** If the bound key should trigger the function when the key is released
    -   **“down”:** If the bound key should trigger the function when the key is pressed
    -   **“both”:** If the bound key should trigger the function when the key is pressed or released

<!-- -->

-   **handlerFunction:** The function that will be triggered when the player's key is pressed. This function should have the form:

  
``` lua
 )
```

The values passed to this function are:

-   **key:** The key that was pressed
-   **keyState:** The state of the key that was pressed, *down* if it was pressed, *up* if it was released.
-   **arguments** The optional arguments you specified when calling [bindKey](/docs/bindKey.md "wikilink") (see below).

</section>
### Optional Arguments

-   **arguments:** Any arguments you may want to pass to the function when the key is pressed by the user. Any number of arguments of can be specified, each being passed to the designated function. You may not pass functions.

### Returns

Returns *true* if the key was bound, *false* otherwise.

### Issues

Example
-------

Example 1

<section name="Server" class="server" show="true">
This example will bind a player's 'F1' key and 'fire' control to 1 input function.

``` lua
function funcInput ( player, key, keyState )
  local state = "let go of"
  if ( keyState == "down" ) then
    state = "pressed"
  end
  outputChatBox ( getPlayerName ( player) .. " " .. state .. " the " .. key .. " key!" )
end

function bindTheKeys ( player, commandName )
  bindKey ( player, "F1", "down", funcInput )   -- bind the player's F1 down key
  bindKey ( player, "F1", "up", funcInput )     -- bind the player's F1 up key
  bindKey ( player, "fire", "both", funcInput ) -- bind the player's fire down and up control
end
addCommandHandler ( "bindme", bindTheKeys )
```

</section>
Example 2

<section name="Client" class="client" show="true">
This example will bind a player's 'F1' key and 'fire' control to 1 input function, clientside.

``` lua
function funcInput ( key, keyState )
  local state = "let go of"
  if ( keyState == "down" ) then
    state = "pressed"
  end
  outputChatBox ( "You " .. state .. " the " .. key .. " key!" )
end

function bindTheKeys ()
  bindKey ( "F1", "down", funcInput )   -- bind the player's F1 down key
  bindKey ( "F1", "up", funcInput )     -- bind the player's F1 up key
  bindKey ( "fire", "both", funcInput ) -- bind the player's fire down and up control
end
addCommandHandler ( "bindme", bindTheKeys )
```

</section>
<section name="Server" class="server" show="true">
This example says how cool is the MTA:SA is if players wants to move.

``` lua
function fanFunction()
  bindKey (source,"forwards","down",
    function(player,key,state)
      outputChatBox (getPlayerName (player) .. "#FFFF00 thinks MTA:SA is so cool.",getRootElement(),255,255,0,true)
    end
  )
end
addEventHandler ("onPlayerLogin",getRootElement(),fanFunction)
```

</section>
See Also
--------
