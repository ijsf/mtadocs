This function returns a random [player](/docs/player.md "wikilink").

Syntax
------

``` lua
player getRandomPlayer ( )
```

### Returns

Returns a random [player](/docs/player.md "wikilink"), *false* if the server is empty.

Example
-------

This code outputs a random player's name.

``` lua
local randomPlayer = getRandomPlayer ( )
outputChatBox ( getPlayerName ( randomPlayer ).." is now the fugitive!" )
```

See Also
--------

[pl:getRandomPlayer](/docs/pl:getRandomPlayer.md "wikilink")
