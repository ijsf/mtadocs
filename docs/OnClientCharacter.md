This event triggers whenever the user presses an alphanumeric character on their keyboard. This also includes special characters, ie. **" / \# % \[ \] { }**.

Parameters
----------

``` lua
string character
```

-   **character**: This represents the pressed character

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the client's [root element](/root_element.md "wikilink").

Example
-------

This example will output the pressed character in the chatbox.

``` lua
function outputPressedCharacter(character)
    if character==" " then --if the character is a space
        character = "space" --change 'character' to 'space'
    end
    outputChatBox("You pressed the character "..character.."!") --output the character
end
addEventHandler("onClientCharacter", getRootElement(), outputPressedCharacter)
```

[pl:onClientCharacter](/pl:onClientCharacter.md "wikilink")

See Also
--------

### GUI events

### Client event functions
