Returns information about how the chatbox looks.

These values come from the file called: [Chatboxpresets.xml](/docs/chatboxpresets.xml.md "wikilink") but it depends on what type of preset you currently have, which is chosen from your settings in the 'Interface' tab.

Syntax
------

``` lua
 )
```

### Optional Arguments

-   **CVar:** the name of the property you want returned. Can be the following values:
    -   **chat\_font** - Returns the chatbox font
    -   **chat\_lines** - Returns how many lines the chatbox has
    -   **chat\_color** - Returns the background color of the chatbox
    -   **chat\_text\_color** - Returns the chatbox text color
    -   **chat\_input\_color** - Returns the background color of the chatbox input
    -   **chat\_input\_prefix\_color** - Returns the color of the input prefix text
    -   **chat\_input\_text\_color** - Returns the color of the text in the chatbox input
    -   **chat\_scale** - Returns the scale of the text in the chatbox
    -   **chat\_width** - Returns the scale of the background width
    -   **chat\_css\_style\_text** - Returns whether text fades out over time
    -   **chat\_css\_style\_background** - Returns whether the background fades out over time
    -   **chat\_line\_life** - Returns how long it takes for text to start fading out
    -   **chat\_line\_fade\_out** - Returns how long takes for text to fade out
    -   **chat\_use\_cegui** - Returns whether CEGUI is used to render the chatbox
    -   **text\_scale** - Returns text scale

### Returns

-   4 numbers if the CVar contains “color”
-   2 numbers if **chat\_scale** was entered
-   1 number if any other CVar was specified
-   a table of all CVar values, if CVar was not specified
-   *false* if an invalid CVar was specified

Example
-------

This code makes the chatbox empty when you type /clear

``` lua
addCommandHandler("clear",
    function ()
        local lines = getChatboxLayout()["chat_lines"]
        for i=1,lines do
            outputChatBox("")
        end
    end
)
```

See Also
--------
