<lowercasetitle></lowercasetitle>

**This function will check if the player have a team then getTheTeamName and do what you want .**

Syntax
------

``` lua
bool DoesPlayerHaveTeam ( player , string TeamName )
```

### Required Arguments

-   **player**: The player whose team you want to find out.
-   **Team Name**: The name team you want to get it from the player .

Code
----

<section name="Function source" class="both" show="true">
``` lua
function DoesPlayerHaveTeam( element,team )
    if ( ( element ) and ( team ) ) then
        if ( isElement ( element ) ) then
            local type = getElementType(element)
            if type ~= "player" then
                outputDebugString ( "Bad argument @ DoesPlayerHaveTeam", 0, 112, 112, 112 ) 
                return false 
            end
            local GetTeam = getPlayerTeam( element )            
            if ( ( GetTeam ) and getTeamName( GetTeam ) == (  team  ) ) then
                return true
            else
                return nil
            end
        end 
    end
end
```

</section>
Example
-------

<section name="Client Example" class="client" show="true">
This Example Will Check if the player wan on the police team and do that function you want .

``` lua
addCommandHandler("Check",
    function (  )
    if ( DoesPlayerHaveTeam ( localPlayer , "Police" ) ) then
        setPedHeadless ( localPlayer , false )
        outputChatBox( "* You Are a Police Officer!",0,0,255 )
    else
        setPedHeadless( localPlayer, true )
        outputChatBox( "* You Are Not a Police Officer!",255,0,0 )
    end
end
)
```

</section>
Example
-------

<section name="Server Example" class="server" show="true">
This Example Will Check if the player wan on the police team and do that function you want .

``` lua
addCommandHandler("Check",
    function ( element )
    if ( DoesPlayerHaveTeam ( element , "Police" ) ) then
        setPedArmor ( element , 100 )
        outputChatBox( "* You Are a Police Officer!",element,0,0,255 )
        outputChatBox( "* You Get 100 % Armor !",element,0,255,0 )
    else
        setPedArmor ( element, 50 )
        outputChatBox( "* You Are Not a Police Officer!",element,255,0,0 )
        outputChatBox( "* You Get 50 % Armor !",element,155,0,0 )
    end
end
)
```

</section>
Example
-------

<section name="Server Full Example With The Source Function" class="server" show="true">
This Example Will Check if the player wan on the police team and do that function you want .

``` lua
local marker = createMarker (  x,y,z,"cylinder",2, 0, 255, 255, 225 )

addEventHandler("onMarkerHit",marker,
    function ( plr )
        if ( getElementType ( plr ) == "player" ) then
        if ( DoesPlayerHaveTeam ( plr , "Police" ) ) then
        outputChatBox("* [Marker] : You Get a Weapon You Are a Police Officer",plr,0,0,255)
        giveWeapon ( plr , 22 , 100 )
        else
        outputChatBox("* [Marker] : For Police Officer Only!",plr,120,0,0)
        end
    end
end
)
        
        
function DoesPlayerHaveTeam( element,team )
    if ( ( element ) and ( team ) ) then
        if ( isElement ( element ) ) then
            local type = getElementType(element)
            if type ~= "player" then
                outputDebugString ( "Bad argument @ DoesPlayerHaveTeam", 0, 112, 112, 112 ) 
                return false 
            end
            local GetTeam = getPlayerTeam( element )            
            if ( ( GetTeam ) and getTeamName( GetTeam ) == (  team  ) ) then
                return true
            else
                return nil
            end
        end 
    end
end
```

</section>
See Also
--------

[Category:Useful Functions](/docs/category:useful_functions.md "wikilink")
