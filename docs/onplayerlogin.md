This event is triggered when a player logs into their account in-game.

Parameters
----------

``` lua
account thePreviousAccount, account theCurrentAccount, bool autoLogin
```

-   **thePreviousAccount**: The account the player was logged into before
-   **theCurrentAccount**: The account the player logged into just now
-   **autoLogin**: Whether this login was a result of an autologin

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the player [element](/docs/element.md "wikilink") that just logged in.

Cancel effect
-------------

If this event is canceled the player will not be logged in.

Example
-------

This example just outputs to the player console that a player in one account logged into an another account:

``` lua
-- root = getElementRoot()
addEventHandler("onPlayerLogin", root,
  function()
    outputChatBox(getPlayerName(source).." has logged in!", root)
  end
)
```

This example allows only hardcoded serials to access given accounts.

``` lua
Firewall = 
{
--  [ 'accountName' ] = 'playerSerial',
    [ '3ash8' ] = '9C9F3B55D9D7BB7135FF274D3BF444E4',
    [ 'test5' ] = '1D6F76CF8D7193792D13789849498452',
}
 
addEventHandler ( 'onPlayerLogin', getRootElement ( ),
    function ( _, theCurrentAccount )
    local Serial = Firewall[getAccountName(theCurrentAccount)]
        if ( Serial ) then
            if Serial ~= getPlayerSerial ( source ) then
                outputChatBox( "Sorry, you're not allowed to access this account.", source)
                cancelEvent( true )
            end
        end
    end
)
```
