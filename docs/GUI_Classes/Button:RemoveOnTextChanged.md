<pageclass class="client" subcaption="GUI Class method"></pageclass>

You can use this method to remove a function that was attached to the sham event with [object:AddOnTextChanged](/GUI_Classes/Button:AddOnTextChanged.md "wikilink"). The function you pass to this method will be removed from the list and will no longer be triggered when text changes.

Syntax
------

``` lua
bool Button:RemoveOnTextChanged ( function func )
```

### Required Arguments

-   **func:** the function you want to remove from the list of functions triggered when text changes

### Returns

-   **true** if function was removed successfully
-   **false** otherwise

Example
-------

This example creates a button. The button has two functions attached to it, one is triggered when user clicks the button (to change text on the button) and the other one is triggered when the text has changed then the function is detached and no longer triggered.

``` lua
addEventHandler ( "onClientResourceStart", getResourceRootElement(),
    function( )
        --create a button object
        local button = Button:Create( 0.7, 0.1, 0.2, 0.1, "Hello", true );

        -- and attach a function to the button which changes its text
        button:AddOnClick( changeMyText );

        -- add myTextHasChanged to the list of triggered functions when text changes
        button:AddOnTextChanged( myTextHasChanged );
    end
)

--setup a function to change the text
function changeMyText ( )
    local text = button:Text( ) --get the text from the button
    if text == "Hello" then
        -- if text of button was "Hello", change it to "World!"
        button:Text( "World!" );
        button:Enabled( false );
    end
end

function myTextHasChanged( btn, oldText, newText  )
    -- if new text is "World!" then set a timer which will change it back to old text (in this case "Hello"),
    -- enable the button and remove this function from the stack
    if newText == "World!" then
        setTimer( btn:Text, 2500, 1, oldTex );
        setTimer( btn:Enabled, 2500, 1, true );
    end
    btn:RemoveOnTextChanged( myTextHasChanged );
end
```

See Also
--------

[Back to GUI Classes page](/GUI_Classes.md "wikilink")
