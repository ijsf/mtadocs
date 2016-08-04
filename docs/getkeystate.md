This function determines if a certain key is pressed or not.

**Note:** 'ralt' may trigger both 'ralt' and 'lctrl', this is due to AltGr

Syntax
------

``` lua
bool getKeyState ( string keyName )
```

### Required Arguments

-   **keyName:** The name of the key you're checking state of. See [Key names](/docs/Key_names.md "wikilink").

### Returns

Returns *true* if the specified key is pressed, *false* if it isn't or if an invalid key name is passed.

Example
-------

This clientside example prints a message when “p” is pressed, and a different one for the “control+p” combination.

``` lua
-- define a function that outputs a message if control is pressed, and a different one if it isn't
function printMessageFunction()
    -- if the left or right control keys are pressed, the user has pressed the "control+p" combo
    if getKeyState( "lctrl" ) == true or getKeyState( "rctrl" ) == true then
        outputChatBox ( "You have pressed 'control+p'." )
    -- if none of those were pressed, he just pressed the "p" key
    else
        outputChatBox ( "You have pressed 'p'." )
    end
end
-- bind the "p" key to our function
bindKey( "p", "down", "Print message", printMessageFunction )
```

See Also
--------
