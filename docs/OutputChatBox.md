This outputs the specified text string to the chatbox. It can be specified as a message to certain player(s) or all players.

It can optionally allow you to embed color changes into the string by setting the colorCoded boolean to true. This allows:

``` lua
outputChatBox ( "#FF0000Hello #00FF00World", getRootElement(), 255, 255, 255, true )
```

This will display as: '''<span style='color:red;'>Hello</span> <span style='color:green'>World</span> '''

Syntax
------

<section name="Server" class="server" show="true">
``` lua
 )
```

Required Arguments
------------------

-   **text:** The text string that you wish to send to the chat window. If more than 128 characters it will not be showed in chat.

Optional Arguments
------------------

-   **visibleTo:** This specifies who the chat is visible to. Any players in this element will see the chat message. See [visibility](/visibility.md "wikilink").
-   **r:** The amount of red in the color of the text. Default value is 231.
-   **g:** The amount of green in the color of the text. Default value is 217.
-   **b:** The amount of blue in the color of the text. Default value is 176.
-   **colorCoded:** A boolean value determining whether or not '\#RRGGBB' tags should be used.

Note: The \#RRGGBB format must contain capital letters a-f is not acceptable but A-F is. Default RGB values in this format are: '\#E7D9B0'.

</section>
<section name="Client" class="client" show="true">
``` lua
 )
```

Required Arguments
------------------

-   **text:** The text string that you wish to send to the chat window. If more than 128 characters it will not be showed in chat.

Optional Arguments
------------------

-   **r:** The amount of red in the color of the text. Default value is 231.
-   **g:** The amount of green in the color of the text. Default value is 217.
-   **b:** The amount of blue in the color of the text. Default value is 176.
-   **colorCoded:** A boolean value determining whether or not '\#RRGGBB' tags should be used.

Note: The \#RRGGBB format must contain capital letters a-f is not acceptable but A-F is. Default RGB values in this format are: '\#E7D9B0'.

</section>
Returns
-------

Returns *true* if the message was displayed successfully. Returns *false* if invalid arguments are specified.

Example
-------

<section name="Server" class="server" show="true">
**Example 1:** This example displays a chat message to all users.

``` lua
x = 5
y = 10  
-- Displays the message
outputChatBox ( "I have " .. x .. " apples and " .. y .. " oranges." )
```

**Example 2:** This example outputs a simple colour coded message, “Red White”, where the 'White' is in white colour, and 'Red' is in a red colour.

``` lua
 outputChatBox ( "Red #FFFFFFWhite", getRootElement(), 255, 0, 0, true )
```

**Example 3:** This example allows for coloured chat, according to a player's nametag. This makes use of colour coded outputs.

``` lua
function colouredChat ( message, theType )
    if theType == 0 then --if its normal chat (not /me or teamchat) then
        cancelEvent() --prevent MTA from outputting chat
        message = string.gsub(message, "#%x%x%x%x%x%x", "") --remove any hex tags in a player's chat to prevent custom colours by using lua's string.gsub
        local r,g,b = getPlayerNametagColor ( source ) --get the player's nametag colour
        local chatterName = getPlayerName ( source ) --get his name
        --output a message with the name as his nametag colour, and the rest in white.
        outputChatBox ( chatterName..":#FFFFFF "..message, getRootElement(), r, g, b, true )
    end
end
addEventHandler("onPlayerChat", getRootElement(), colouredChat)
```

**Example 4:** This example displays a chat message to a single user called *someguy*.

``` lua
-- Find the player element for the player called 'someguy'
myPlayer = getPlayerFromName ( "someguy" )
-- If a player was found called 'someguy' then...
if ( myPlayer ~= false ) then
    x = 5
    y = 10
    -- Display the message
    outputChatBox ( "I have " .. x .. " apples and " .. y .. " oranges.", myPlayer )
end
```

**Example 5:** These two functions can speed up typing, and display a message when a player Joins.

``` lua
local msg_red,msg_green,msg_blue = 255,255,0

function servertalkprivate(message, sendto)
        --Talk to one client only
    outputChatBox(tostring(message), sendto, msg_red, msg_green, msg_blue, true)
end

function servertalk(message)
        --Talk to everyone
    servertalkprivate(message, getRootElement())
end

function onJoin()
    servertalkprivate("Welcome to My Server", source)
end

addEventHandler("onPlayerJoin",getRootElement(),onJoin)
```

**Example 6:** This can be used to display a message when the player joins and sets its armor to 100. **(By Bilal135)**

``` lua
function onJoin()
         setPedArmor(source, 100)
         outputChatBox("Welcome To The Server", source, 255, 0, 0)
end
addEventHandler("onPlayerJoin", root, onJoin)
```

</section>
See Also
--------

[cs:outputChatBox](/cs:outputChatBox.md "wikilink") [pl:outputChatBox](/pl:outputChatBox.md "wikilink") [ru:outputChatBox](/ru:outputChatBox.md "wikilink")
