This function is for setting the color of a specified team. This color is shown, for example, in the team players' nametags.

Syntax
------

``` lua
bool setTeamColor ( team theTeam, int colorR, int colorG, int colorB )
```

### Required Arguments

-   **theTeam:** The [team](/docs/team.md "wikilink") you want to change the color of.
-   **colorR:** An integer representing the red color value, from 0 to 255.
-   **colorG:** An integer representing the green color value, from 0 to 255.
-   **colorB:** An integer representing the blue color value, from 0 to 255.

### Returns

Returns *true* if the team is valid and the color is different, otherwise *false*.

Example
-------

This example creates a new team then changes its name and color.

``` lua
team = createTeam ( "RedTeam", 255, 0, 0 ) -- create the team
if ( team ) then                           -- if the team was created (a team with that name didn't already exist)
    setTeamName ( team, "BlueTeam" )       -- change the name
    setTeamColor ( team, 0, 0, 255 )       -- change the color to suit its new name
end
```

See Also
--------
