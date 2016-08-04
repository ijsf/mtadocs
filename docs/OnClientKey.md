This event triggers whenever the user presses a button on their keyboard or mouse. This event can also be used to see if the client scrolls his mousewheel.

Parameters
----------

``` lua
string button, bool pressOrRelease
```

-   **button**: This refers the button pressed. see [Key names](/Key_names.md "wikilink") for list of keys string
-   **pressOrRelease**: This refers to whether they were pressing or releasing the key, true when pressing, false when releasing.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the client's [root element](/root_element.md "wikilink").

Cancel effect
-------------

Example
-------

This example will say in chatbox every time the user presses down a a key.

``` lua
function playerPressedKey(button, press)
    if (press) then -- Only output when they press it down
        outputChatBox("You pressed the "..button.." key!")
    end
end
addEventHandler("onClientKey", root, playerPressedKey)
```

This example outputs if the client moves his mousewheel.

``` lua
addEventHandler( "onClientKey", root, function(button,press) 
    -- Since mouse_wheel_up and mouse_wheel_down cant return a release, we dont have to check the press.
    if button == "mouse_wheel_up" or button == "mouse_wheel_down" then
        outputDebugString( button .. " moved." )
        return true
    end
    return false
end )
```

[pl:onClientKey](/pl:onClientKey.md "wikilink")

See Also
--------

### GUI events

### Client event functions
