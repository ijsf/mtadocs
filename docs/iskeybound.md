This function can be used to find out if a key has already been bound.

Syntax
------

``` lua
 ) 
```

### Required Arguments

-   **thePlayer:** The player you're checking.
-   **key:** The key you're checking. See [Key names](/docs/key_names.md "wikilink") for a list of valid key names.

### Optional Arguments

-   **keyState:** Is the state of the key when it calls the function, Can be either:
    -   **“up”:** when the key is released
    -   **“down”:** when the key is pressed
-   **handler:** The function you're checking against

Note: If you do not specify a *keyState* or *handler*, any instances of *key* being bound will cause *isKeyBound* to return *true*.

Example
-------

``` lua
-- This function tells everyone in the server if someone has numpad 9 bound!
function onPlayerJoin ()
  if (isKeyBound (source,"num_9")) then -- if num pad 9 is bound
    outputChatBox (getPlayerName (source) .. " has bound numpad 9!",getRootElement(),255,0,0,false) -- let see everybody that he has binded it
  end
end
addEventHandler ("onPlayerJoin",getRootElement(),onPlayerJoin) -- add event.
```

See Also
--------
