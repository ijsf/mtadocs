Sends message to gang member chat.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool outputGangChat ( string Gang, string AccountName, string PlayerName, string Message )
```

Required Arguments
------------------

-   **Gang:** ID of the gang you wish to output message to
-   **AccountName:** Name of the account that is the source of the message (can be any string)
-   **PlayerName:** Name of the player that is the source of the message (can be any string)
-   **Message:** Message to output to gang chat

</section>
<section name="Client" class="client" show="true">
``` lua
bool outputGangChat ( string Gang, string AccountName, string PlayerName, string Message )
```

Required Arguments
------------------

-   **Gang:** ID of the gang you wish to output message to
-   **AccountName:** Name of the account that is the source of the message (can be any string)
-   **PlayerName:** Name of the player that is the source of the message (can be any string)
-   **Message:** Message to output to gang chat

</section>
Returns
-------

-   **Success:** Boolean that is true if message was successfully sent or false otherwise
