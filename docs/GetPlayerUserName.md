This function returns the community.mtasa.com (or mtabeta.com) account of the specified user.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
string getPlayerUserName ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") whose MTA account username you want to retrieve.

### Returns

A *string* value containing the MTA account username or *false* if no account exists for the player.

</section>
<section name="Client" class="client" show="true">
``` lua
string getPlayerUserName ()
```

### Returns

A *string* value containing local player's MTA account username or *false* if no account exists for the local player.

</section>
Example
-------

<section name="Server" class="server" show="true">
``` lua
function outputMTAAccount ( sourcePlayer )
        -- if the command was triggered by an ingame player
        if ( sourcePlayer ) then
                local mtaaccount = getPlayerUserName( sourcePlayer )
                if ( mtaaccount ) then
                        outputChatBox("Your community.mtasa.com account is " .. mtaaccount, sourcePlayer )
                else
                        outputChatBox("Can't find an account for you.", sourcePlayer )
                end
        end
end


-- register outputMTAAccount as a handler for the mta-account command
addCommandHandler ( "mtaaccount", outputMTAAccount )
```

</section>
See Also
--------
