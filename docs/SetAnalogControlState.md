This sets the analog control state of a control for the local player.

To change the analog controls for a ped, please use [setPedAnalogControlState](/setPedAnalogControlState.md "wikilink").

Syntax
------

``` lua
 ) 
```

### Required Arguement

-   **controlName**: the control name you wish to set the analog state of. Here's a list:
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

### Optional Arguments

-   **state:** A float between 0 and 1 indicating the amount the control is pressed. If no value is provided, the analog control is removed.

### Returns

Returns true, else false if invalid argument.

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
