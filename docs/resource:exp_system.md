A level/experience system made from scratch by [Castillo](/docs/user:castillo.md "wikilink").
It uses SQLite to save level and experience.

Exported Functions
==================

<section name="Server" class="server" show="true">
This function is used to get a player level.

Syntax
------

``` lua
bool getPlayerLevel ( player thePlayer )
```

Required Arguments
------------------

-   **thePlayer**: The player element you wish you get the level.

Returns
-------

Returns a number with the level of the player.

``` lua
addCommandHandler ( "mylevel",
    function ( thePlayer )
                local myLevel = exports.exp_system:getPlayerLevel ( thePlayer )
        outputChatBox ( "Your level is: ".. myLevel, thePlayer )
    end
)

</section>

<section name="Server" class="server" show="true">
This function is used to set a player level.

==Syntax==
<syntaxhighlight lang="lua">
bool setPlayerLevel ( player thePlayer, int theLevel )
```

Required Arguments
------------------

-   **thePlayer**: The player element you wish you set the level.
-   **theLevel**: The level you want to set.

Returns
-------

Returns a bool, whether the level was set successfully or not.

``` lua
addCommandHandler ( "setmylevel",
    function ( thePlayer, commandName, theLevel )
                local theLevel = tonumber ( theLevel ) or 1
        exports.exp_system:setPlayerLevel ( thePlayer, theLevel )
    end
)
</section>

<section name="Server" class="server" show="true">
This function is used to get a player experience.

==Syntax==
<syntaxhighlight lang="lua">
bool getPlayerEXP ( player thePlayer )
```

Required Arguments
------------------

-   **thePlayer**: The player element you wish you get the experience.

Returns
-------

Returns a number with with the experience of the player.

Example
-------

``` lua
addCommandHandler ( "myexp",
    function ( thePlayer )
                local myExp = exports.exp_system:getPlayerEXP ( thePlayer )
        outputChatBox ( "Your experience is: ".. myExp, thePlayer )
    end
)
</section>
<section name="Server" class="server" show="true">
This function is used to set a player experience.

==Syntax==
<syntaxhighlight lang="lua">
bool setPlayerEXP ( player thePlayer, int theExperience )
```

Required Arguments
------------------

-   **thePlayer**: The player element you wish you set the experience.
-   **theExperience**: The exprience you want to set.

Returns
-------

Returns a bool, whether the experience was set successfully or not.

Example
-------

``` lua
addCommandHandler ( "setmyexp",
    function ( thePlayer, commandName, theExp )
                local theExp = tonumber ( theExp ) or 0
        exports.exp_system:setPlayerEXP ( thePlayer, theExp )
    end
)
</section>
<section name="Server" class="server" show="true">
This function is used to give a player experience.

==Syntax==
<syntaxhighlight lang="lua">
bool addPlayerEXP ( player thePlayer, int theExperience )
```

Required Arguments
------------------

-   **thePlayer**: The player element you wish you to give the experience.
-   **theExperience**: The exprience you want to give.

Returns
-------

Returns a bool, whether the experience was given successfully or not.

Example
-------

``` lua
addEvent ( "onZombieWasted", true )
addEventHandler ( "onZombieWasted", root,
    function ( theKiller )
        exports.exp_system:addPlayerEXP ( theKiller, 5 )
    end
)
</section>
<section name="Server" class="server" show="true">
This function is used to get an account level.

==Syntax==
<syntaxhighlight lang="lua">
bool getAccountLevel ( account theAccount )
```

Required Arguments
------------------

-   **theAccount**: The player element you wish you get the level.

Returns
-------

Returns a number with with the level of the account.

``` lua
addCommandHandler ( "mylevel",
    function ( thePlayer )
        local account = getPlayerAccount ( thePlayer )
                local myExp = exports.exp_system:getAccountLevel ( account )
        outputChatBox ( "Your account level is: ".. myLevel, thePlayer )
    end
)

</section>

<section name="Server" class="server" show="true">
This function is used to set an account level.

==Syntax==
<syntaxhighlight lang="lua">
bool setAccountLevel ( account theAccount, int theLevel )
```

Required Arguments
------------------

-   **theAccount**: The player element you wish you set the level.
-   **theLevel**: The level you want to set.

Returns
-------

Returns a bool, whether the level was set successfully or not.

``` lua
addCommandHandler ( "setmylevel",
    function ( thePlayer, commandName, theLevel )
        local account = getPlayerAccount ( thePlayer )
                local theLevel = tonumber ( theLevel ) or 1
        exports.exp_system:setAccountLevel ( account, theLevel )
    end
)
</section>

<section name="Server" class="server" show="true">
This function is used to get an account experience.

==Syntax==
<syntaxhighlight lang="lua">
bool getAccountEXP ( account theAccount )
```

Required Arguments
------------------

-   **theAccount**: The player element you wish you get the experience.

Returns
-------

Returns a number with with the experience of the player.

Example
-------

``` lua
addCommandHandler ( "myexp",
    function ( thePlayer )
        local account = getPlayerAccount ( thePlayer )
                local myExp = exports.exp_system:getAccountEXP ( account )
        outputChatBox ( "Your account experience is: ".. myExp, thePlayer )
    end
)
</section>
<section name="Server" class="server" show="true">
This function is used to set an account experience.

==Syntax==
<syntaxhighlight lang="lua">
bool setAccountEXP ( account theAccount, int theExperience )
```

Required Arguments
------------------

-   **theAccount**: The player element you wish you set the experience.
-   **theExperience**: The exprience you want to set.

Returns
-------

Returns a bool, whether the experience was set successfully or not.

Example
-------

``` lua
addCommandHandler ( "setmyexp",
    function ( thePlayer, commandName, theExp )
        local account = getPlayerAccount ( thePlayer )
                local theExp = tonumber ( theExp ) or 0
        exports.exp_system:setAccountEXP ( account, theExp )
    end
)
</section>

<section name="Server" class="server" show="true">
This function is used to refresh the levels.

==Syntax==
<syntaxhighlight lang="lua">
bool loadLevelsFromXML( )
```

Required Arguments
------------------

-   **None**

Example
-------

``` lua
addCommandHandler ( "refreshlevels",
    function ( )
        exports.exp_system:loadLevelsFromXML ( )
    end
)
</section>

<section name="Server" class="server" show="true">
This function is used to obtain the name and experience required of a level.

==Syntax==
<syntaxhighlight lang="lua">
getLevelData ( int theLevel )
```

Required Arguments
------------------

-   **theLevel**

Returns
-------

Returns the name of the level and the experience required.

Example
-------

``` lua
addCommandHandler ( "getleveldata",
    function ( thePlayer )
        local level = exports.exp_system:getPlayerLevel ( thePlayer )
        local name, expreq = exports.exp_system:getLevelData ( level )
        outputChatBox ( name ..": ".. expreq, thePlayer )
    end
)
</section>

=Custom Events=

<section name="Server" class="server" show="true">
This event is called when a player level changes.

==Syntax==
<syntaxhighlight lang="lua">
event onPlayerChangeLevel
```

Parameters
----------

-   **oldLevel**: The player old level.
-   **newLevel**: The player new level.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") whose level changed.

</section>
<section name="Server" class="server" show="true">
This event is called when a player level UP.

Syntax
------

``` lua
event onPlayerLevelUP
```

Parameters
----------

-   **oldLevel**: The player old level.
-   **newLevel**: The player new level.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") who leveled UP.

</section>
See also
========

[Download page](http://community.mtasa.com/index.php?p=resources&s=details&id=1253)
[Category:Resource](/docs/category:resource.md "wikilink")
