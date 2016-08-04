This retrieves the analog control state of a control. This is useful for detecting sensitive controls, such as those used on a joypad.

Syntax
------

``` lua
float getAnalogControlState ( string controlName )
```

### Required Arguments

-   **controlName :** the name of the control you wish to get the analog state of. Possible values are:
    -   **left**
    -   **right**
    -   **forwards**
    -   **backwards**
    -   **vehicle\_left**
    -   **vehicle\_right**
    -   **steer\_forward**
    -   **steer\_back**
    -   **accelerate**
    -   **brake\_reverse**
    -   **special\_control\_left**
    -   **special\_control\_right**
    -   **special\_control\_up**
    -   **special\_control\_down**

### Returns

Returns a float between 0 and 1 indicating the amount the control is pressed.

Example
-------

/analog command starts to go forward control state if you are not, if you are going forward by control state then you will stop.

``` lua
function analog()
if (getAnalogControlState("forwards") == 0) then
setAnalogControlState ("forwards",1)
else
setAnalogControlState ("forwards",0)
end
end
addCommandHandler("analog",analog)
```

This example written by **Samurai**

See Also
--------
