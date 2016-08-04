Gets the commands bound to a key.

Syntax
------

``` lua
table getCommandsBoundToKey ( string theKey, string keyState )
```

### Required Arguments

-   **theKey:** See [key names](/key_names.md "wikilink") for a list of possible keys
-   **keyState:** A string that has one of the following values:
    -   **“up”:** If the bound key should trigger the function when the key is released
    -   **“down”:** If the bound key should trigger the function when the key is pressed

### Returns

Returns a table of the commands bound on that key.

Example
-------

<section name="Client" class="client" show="true">
This example adds the command /keycommands <theKey> <keyState>

``` lua
addCommandHandler ( "keycommands",
    function ( commandName, theKey, keyState )
        if ( theKey and keyState ) then -- We check if theKey and keyState is valid.
            local commands = getCommandsBoundToKey ( theKey, keyState )
            if ( commands and type ( commands ) == "table" ) then
                for command, state in pairs ( commands ) do
                    outputChatBox ( command )
                end
            end
        else
            outputChatBox ( commandName ..": Correct syntax: [ theKey ] [ keyState ]" )
        end
    end
)
```

</section>
See Also
--------
