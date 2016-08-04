This function sets or removes masking (covering up the text being typed) for password text fields.

Syntax
------

``` lua
bool guiEditSetMasked ( element theElement, bool status )
```

### Required Arguments

-   **theElement:** The edit box to be changed.
-   **status:** A boolean value indicating whether masking is to be enabled or disabled.

### Returns

Returns *true* if the function is successful, *false* otherwise.

Example
-------

This example creates an edit box and an OK button. The user types in his password, and it checks if the password was correct

``` lua
-- set our password
password = "cheeseman"

-- create our button
button = guiCreateButton( 0.7, 0.1, 0.2, 0.1, "OK", true )
-- create an edit box and define it as "editBox"
editBox = guiCreateEdit( 0.3, 0.1, 0.4, 0.1, "", true )
-- ensure that it is masked
guiEditSetMasked ( editBox, true )

-- set up our function to output the message to the chatbox
function checkPassword ()
        local text = guiGetText ( editBox )     -- get the text from the edit box
        if text == password then                -- if the text matches the password
                outputChatBox ( "Password Correct!" )
        else
                outputChatBox ( "Password Incorrect!" )
        end
end
-- set the function to be called when the OK button is clicked
addEventHandler ( "onClientGUIClick", button, checkPassword )
```

See Also
--------
