This event is triggered when a user logs out of their account in-game.

Parameters
----------

``` lua
account thePreviousAccount, account theCurrentAccount
```

-   **thePreviousAccount**: The account the client was logged in as
-   **theCurrentAccount**: The account the client is a part of now (usually a guest account)

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the client [element](/element.md "wikilink") that logged out. For example a player.

Example
-------

This example displays a message if the client logs out.

``` lua
function loggedOut()
    outputChatBox( "You have successfully logged out!", source )
end
addEventHandler("onClientLogout",getRootElement(),loggedOut)
```
