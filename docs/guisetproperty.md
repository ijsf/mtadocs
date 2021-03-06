This function sets the value of a specific CEGUI property of a GUI element. For a list of properties and their meaning, see the [CEGUI Properties Wiki Page (Wayback Machine)](http://web.archive.org/web/20120706081430/http://cegui.org.uk/static/WindowsLookProperties.html).

Syntax
------

``` lua
bool guiSetProperty ( element guiElement, string property, string value )
```

### Required Arguments

-   **guiElement:** the GUI element you wish to get a property of.
-   **property:** the name of of property you want the value of.
-   **value:** the new value for the property.

### Returns

If the function succeeds it returns *true*, if it fails it returns *false*.

Example
-------

This example creates a button when the resource starts and defines a console command that toggles it between enabled (clickable) and disabled (not clickable).

``` lua

function onStart()
  button = guiCreateButton( 20, 200, 150, 30, "Test", false )
end
addEventHandler( "onClientResourceStart", getResourceRootElement(), onStart )

function toogleButton()
  local currentState = guiGetProperty( button, "Disabled" )
  if currentState == "False" then
    guiSetProperty( button, "Disabled", "True" )
  else
    guiSetProperty( button, "Disabled", "False" )
  end
end
addCommandHandler( "togglebtn", toogleButton )
```

See Also
--------
