<pageclass class="client" subcaption="GUI Class method"></pageclass>

This method allows you to set/get a color of label on the button when you hover over it.

Syntax
------

``` lua
bool Button:ColorOnHover ( string hex )
```

``` lua
string Button:ColorOnHover ( )
```

### Required Arguments

-   **hex:** hexadecimal string of the new color (format is “RRGGBBAA”, red, green, blue, alpha)

### Returns

-   **true** if color was changed successfully (used “set”)
-   **string** of color (used “get”)
-   **false** otherwise.

Example
-------

This example creates an edit box alongside an “Output!” button. When the button is clicked, it will output the message in the text box into the Chat Box.

Color of the label on button will change.

``` lua
addEventHandler ( "onClientResourceStart", getResourceRootElement(),
    function( )
        --create a button object
        local button = Button:Create( 0.7, 0.1, 0.2, 0.1, "Output!", true );
        -- change the color when cursor is moved on top of the button
        button:ColorOnHover( "FF0000FF" );
        --Create a TextBox (formally edit box)
        textBox = TextBox:Create( 0.3, 0.1, 0.4, 0.1, "Type your message here!", true )
        textBox:MaxLength( 128 ) --the max chatbox length is 128, so force this

        -- and attach the outputTextBox function to the button
        button:AddOnClick( outputTextBox );
    end
)
--setup our function to output the message to the chatbox
function outputTextBox( )
        local text = textBox:Text( ) --get the text from the TextBox
        outputChatBox ( text ) --output that text
end
```

See Also
--------

[Back to GUI Classes page](/GUI_Classes.md "wikilink")
