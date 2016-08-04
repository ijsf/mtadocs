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

The [source](/event_system#Event_source.md "wikilink") of this event is the player that logged out.

Cancel effect
-------------

If you cancel this event the player will not be logged out.

Example
-------

This example displays a message if the player logs out.

``` lua
function loggedOut()
    outputChatBox( "You have successfully logged out!", source )
end
addEventHandler("onPlayerLogout",getRootElement(),loggedOut)
```
