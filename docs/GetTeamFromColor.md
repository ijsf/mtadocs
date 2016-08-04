<lowercasetitle/>

This function gets a team from it's color. **Note:** If 2 teams has the same color, then the first one found will be returned!

Syntax
------

``` lua
team getTeamFromColor ( int r, int g, int b)
```

### Required Arguments

-   **r**: The red color.
-   **g**: The green color.
-   **b**: The blue color.

### Return

Returns a [team](/team.md "wikilink") else false if bad arguments were given or a team doesn't have the same color.

Code
----

``` lua
function getTeamFromColor(r,g,b)
    if 
        not r or type(r)~="number" or r<0 or r>255 or
        not g or type(g)~="number" or g<0 or g>255 or
        not b or type(b)~="number" or b<0 or b>255
    then outputDebugString("getTeamFromColor - Bad Arguments",0) return false end
        
    for _,team in ipairs(getElementsByType("team"))do
        local tR,tG,tB = getTeamColor(team)
        if tR==r and tG==g and tB==b then
            return team
        end
    end
    return false
end
```

Example
-------

Author: Jaysds1

See Also
--------
