This function retrieves a players ASE announce value under a certain key.

Syntax
------

``` lua
string getPlayerAnnounceValue ( element thePlayer, string key )
```

### Required Arguments

-   **thePlayer:** This is the [Player](/docs/player.md "wikilink") whos value you want to retrieve.
-   **key:** The name of the key.

### Returns

This function returns a *string* containing the requested value if a valid key was specified or *false* otherwise.

Example
-------

This example adds a command named “getscore” which outputs a players “score” value to his chatbox.

``` lua
function getScore ( playerSource, cmdName )
    local scoreValue = getPlayerAnnounceValue ( playerSource, "score" )
    if ( scoreValue ) then
        outputChatBox ( "Your score: "..scoreValue, playerSource )
    end
end

addCommandHandler ( "getscore", getScore )
```

See Also
--------

[Category:Changes\_in\_1.0](/docs/category-changes_in_1.0.md "wikilink")
