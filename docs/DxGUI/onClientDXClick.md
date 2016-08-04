This event is triggered when you click a dx element.

Parameters
----------

``` lua
string button, string state, int absoluteX, int absoluteY
```

-   **button:** the name of the dx element which will be clicked , it can be *left*, *right*, *middle*
-   **state:** the state of the mouse button, will be *down* if the mouse button was pushed, or *up* if it was released. '''
-   **absoluteX:** the X position of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY:** the Y position of the mouse cursor, in pixels, measured from the top of the screen.

### Source

The [source](/event_system#Event_source.md "wikilink") of this event is the DX element that was clicked.

Example
-------

**Example 1:** This example outputs when you click a dx elements.

``` lua
addEvent( "onClientDXClick", true )
addEventHandler( "onClientDXClick", root, function()
   outputChatBox("You clicked a dx element")
end
)
```
