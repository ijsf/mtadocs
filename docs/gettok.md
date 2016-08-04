This function splits a string using the given separating character and returns one specified substring.

Syntax
------

``` lua
string gettok ( string text, int tokenNumber, string / int separatingCharacter )
```

### Required Arguments

-   **text:** the string that should be split.
-   **tokenNumber:** which token should be returned (1 for the first, 2 for the second, and so on).
-   **separatingCharacter:** the [ASCII number](/docs/ascii.md "wikilink") representing the character you want to use to separate the tokens. You can easily retrieve this by running string.byte on a string containing the separating character.

### Returns

Returns a [string](/docs/string.md "wikilink") containing the token if it exists, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example retrieves the startskin and endskin for spawning a player from a string of two numbers “a,b”

``` lua
-- Put the string with the skins in a variable. Normally you would read it from a .map file or something.
local skins = "20,30"
-- Get the startskin and endskin strings ("20" and "30" in this case)
local startskin = gettok ( skins, 1, string.byte(',') )
local endskin = gettok ( skins, 2, string.byte(',') )
-- Get a random skin in the range
local skin = math.random ( tonumber(startskin), tonumber(endskin) )
```

</section>
See Also
--------
