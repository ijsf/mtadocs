This function returns the current text of the specified [textitem](/docs/textitem.md "wikilink").

Syntax
------

``` lua
string textItemGetText ( textitem theTextitem )             
```

### Required Arguments

-   **theTextitem:** A valid [textitem](/docs/textitem.md "wikilink").

### Returns

Returns a [string](/docs/string.md "wikilink") containing the text if the function was successful, *false* otherwise.

Example
-------

Increment a score display. In real scripts it's of course better to keep a global 'score' variable which can be incremented directly.

``` lua
function givePoint ( thePlayer )
    local scoretextitem = scoretextitems[thePlayer]    -- find the score text item that belongs to this player
    local score = textItemGetText ( scoretextitem )    -- read the text (a score number)
    score = tostring(tonumber(score) + 1)              -- convert to number, add 1, convert to text
    textItemSetText ( scoretextitem, score )           -- put the new score on the text item
end
```

See Also
--------
