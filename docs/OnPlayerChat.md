This event is triggered when a player chats inside the chat box.

Parameters
----------

``` lua
string message, int messageType
```

-   **message**: A string representing the message typed into the chat.
-   **messageType**: An integer value representing the message type:
    -   **0**: normal message
    -   **1**: action message (/me)
    -   **2**: team message

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") who sent the chatbox message.

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), the game's chat system won't deliver the posts. You may use [outputChatBox](/outputChatBox.md "wikilink") to send the messages then. Cancelling this event also means the chat will not appear in the server console or logs. If you want chat logging, you will have to add a call to [outputServerLog](/outputServerLog.md "wikilink") - See the second example.

Examples
--------

<section name="Example 1" class="server" show="true">
This example limits receiving of chat messages to a spherical area around the player who sent the message, also blocking action and team text.

``` lua
-- define our chat radius
local chatRadius = 20 --units

-- define a handler that will distribute the message to all nearby players
function sendMessageToNearbyPlayers( message, messageType )
    -- we will only send normal chat messages, action and team types will be ignored
    if messageType == 0 then
        -- get the chatting player's position
        local posX, posY, posZ = getElementPosition( source )
        
        -- create a sphere of the specified radius in that position
        local chatSphere = createColSphere( posX, posY, posZ, chatRadius )
        -- get a table all player elements inside it
        local nearbyPlayers = getElementsWithinColShape( chatSphere, "player" )
        -- and destroy the sphere, since we're done with it
        destroyElement( chatSphere )
        
        -- deliver the message to each player in that table
        for index, nearbyPlayer in ipairs( nearbyPlayers ) do
            outputChatBox( message, nearbyPlayer )
        end
    end
end
-- attach our new chat handler to onPlayerChat
addEventHandler( "onPlayerChat", getRootElement(), sendMessageToNearbyPlayers )

-- define another handler function that cancels the event so that the message won't be delivered through the 
function blockChatMessage()
    cancelEvent()
end
-- attach it as a handler to onPlayerChat
addEventHandler( "onPlayerChat", getRootElement(), blockChatMessage )
```

</section>
<section name="Example 2" class="server" show="true">
This example implements colored player names in chat.

``` lua
--This function is executed when a player joins, it sets the player's name-tag color to a random color.
local function playerJoin()
    local red, green, blue = math.random (50, 255), math.random (50, 255), math.random (50, 255)
        setPlayerNametagColor(source, red, green, blue)
end
addEventHandler ("onPlayerJoin", root, playerJoin)

--This function is executed when a player says something in chat, it outputs the player's message, with their nick colored to match their name tag color.
local function playerChat(message, messageType)
    if messageType == 0 then --Global (main) chat
                cancelEvent()
                local red, green, blue = getPlayerNametagColor(source)
        outputChatBox(getPlayerName(source)..": #FFFFFF"..message, root, red, green, blue, true )
        outputServerLog("CHAT: "..getPlayerName(source)..": "..message)--NOTE: Beacuse we cancelled the onPlayerChat event, we need to log chat manually.
    end
end
addEventHandler("onPlayerChat", root, playerChat)
```

</section>
