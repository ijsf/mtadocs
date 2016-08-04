Alpha represents the transparency of a gui element. This function allows retrieval of a gui element's current alpha.

Syntax
------

``` lua
float guiGetAlpha ( element guiElement )
```

### Required Arguments

-   **guiElement:** The gui element in which you want to retrieve the alpha of.

### Returns

This function returns a positive integer in between 0 and 1 of the gui element's current alpha, or false if it could not be retrieved.

Example
-------

This example provides a *guiFade* function, which allows you to fade in/out a GUI.

``` lua
function guiFade( gui, state )
    if state == "in" then -- This state will fade IN the GUI
    fadeIn = setTimer(guiFade, 50, 1, gui, state) -- We loop the function to make it lower the alpha each 50 ms
    alpha = guiGetAlpha(gui) -- We get the GUI's actual alpha after each loop
    guiSetAlpha(gui, alpha - 0.1) -- We set the GUI's actual alpha after each loop
    if alpha == 0 then -- If the loop reached "0"...
        guiSetVisible(gui, false) -- We set the GUI visibility to 0 so it won't be clickable or editable
        killTimer(fadeIn) -- ... We kill the timer
        fadeIn = nil -- And to make sure it doesn't exist anymore, we set it to nil
        end
    elseif state == "out" then -- This state will fade OUT the GUI
        guiSetVisible(gui, true) -- Since the GUI will still be click-able, we'll set it's visibility to "false"
        fadeOut = setTimer(guiFade, 50, 1, gui, state) -- We loop the function to make it higher the alpha each 50 ms
        alpha = guiGetAlpha(gui) -- We get the GUI's actual alpha after each loop
        guiSetAlpha(gui, alpha + 0.1) -- We set the GUI's actual alpha after each loop
        if alpha == 1 then -- If the loop reached "1"...
            killTimer(fadeOut) -- ... We kill the timer
            fadeOut = nil -- And to make sure it doesn't exist anymore, we set it to nil
        end
    end
end

-- NOTE: If you're using a button to pop up the GUI-Element. Use "guiSetEnabled" along with the button. You'll have also to set a timer in order to disable it by the time it fades, either way it will bug.
```

See Also
--------
