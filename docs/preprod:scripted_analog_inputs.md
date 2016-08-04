Proposed names
==============

All functions used in the binds system use either **control names** or **key names**. Here are proposed names for the new analog variants:

### Controls

Since analog controls are shared both on foot and in vehicle, two different sets are not required.

-   **move\_x**: This represents moving your left analog stick left/right. Return values are -1 &lt;= n &lt;= 1.
-   **move\_y**: This represents moving your left analog stick up/down. Return values are -1 &lt;= n &lt;= 1.
-   **look\_x**: This represents moving your right analog stick left/right. Return values are -1 &lt;= n &lt;= 1.
-   **look\_y**: This represents moving your right analog stick up/down. Return values are -1 &lt;= n &lt;= 1.
-   **accelerate**: A special analog accelerate that is sensitive. Return values are 0 &lt;= n &lt;= 1. Accelerate only acts upon a single direction
-   **brake\_reverse**: A special analog brake/reverse that is sensitive. Return values are 0 &lt;= n &lt;= 1. Brake only acts upon a single direction

### Other input

These arent “keys” as such anymore, so i'm labelling them “Other” here. These cannot be *set* at any point, only binded to or get'd. These are ripped from ccw's current definitions, and i cant confirm return values. I'm guessing what they represent based upon my own controller

-   **axis\_x**: This mostly represents left analog stick left/right.
-   **axis\_y**: This mostly represents left analog stick up/down.
-   **axis\_z**: This mostly represents right analog stick up/down.
-   **axis\_rz**: This mostly represents right analog stick left/right.
-   **axis\_ry**:
-   **axis\_ry**:
-   **axis\_rz**:
-   **sld**: A trigger button.

get/setAnalogInputState
=======================

This is the first, and perhaps the most straightforward set of functions to be implemented. These are similar to get/setControlState, with a few key differences:

-   1) Clearly it gets/sets the states of **analog** inputs. This means returning and setting accurate floats instead of bools, with a range of -1 and 1, where negative is backwards across an axis and positive is forwards
-   2) Similar to bindKey, this function will be used for both “Keys” and “Controls”. This means that unlike getControlState, it will work for both types of input.

Right now MTA's internal get/setControlState use analog inputs, and force them to a value of 255. Hopefully this means that implementing these is a matter of adding custom input levels.

bindKey
=======

bindKey is based upon binding to “up” and “down” states. Therefore it is illogical to bind to a float “0.141516516” state. Instead, based upon configured deadzones, an artifical “up” and “down” state will be replicated:

-   **down**: No input is being recieved from this input.
-   **up**: An input of *any* value is being recieved from the controller.

This will allow scripters to use these as 'events' to add their own onClientRender event handlers to handle the specific level of sensitivity.

toggleControl
=============

This would not be very complex but quite simple - it would function exactly as it does now with added functionality to toggle off analog controls.

Serverside scripting
====================

Depending on the amount of data that is actually synced, (i believe control states are synced), serverside functions can be replicated. I believe all analog controls are synced. Clearly, like KeyStates, you will not be able to retrieve “Other” inputs serverside.

Flaws
=====

Naming & Purpose
----------------

“set/getAnalogInputState” seems an excuse to merge two different sets of input together. There are various flaws, even if we just think of documentation:

-   “Other”'s cant be used for setAnalogInputState.
-   “Other”'s cant be used for serverside bindKey.
-   Renaming to *\*AnalogControlState* may seem sensible, but it raises the question of what we name the other set of inputs. This was easy for getControlState - they were Keys so it could become getKeyState.

Mouse input
-----------

This raises a big question of something that is missing from MTA. Technically, Mouse Input is an analog input - it is a “detailed” input method that cannot be accounted for with our current functions, but would make sense using the new analog inputs proposal. Implementing this has many advantages, for example fixing Mantis \#3040 and \#3966. Another example is the fact that mouse aim cannot be replicated by script. However, there are various issues which (most likely) make this difficult:

-   Mouse input doesnt appear to be implemented into MTA at all. Although we have events like onClientCursorMove, we dont have any functions that interface with GTA directly. In other words, there doesnt appear to be any code for MTA to allow *setting* the aim, for it to be part of keybinds in the first place. The whole mouse aim seems to be GTA's own mouse aim, left untouched and detached from the binds system
-   It is unlike any other input: The keybinds system is nice in the way that all controls are implemented using the same system. In the case of the mouse, it would (afaik) require a completely renewed system specifically for mouse input. This input would be moulded into the Scripted Analog Input system, rather than already being part of it.

However, it can be argued that since we have Mouse input functions already, this is not a big deal. In answer to that, i would give this example:

    You've just written paralysis script.  The driver cannot turn while driving but can only accelerate (As seen in the mini gamemode 'Chicken').  A player then goes to settings, turns on "Steer with mouse", and is now able to get around any  control toggling that may have been done.   In order to detect this, some dodgy mouse input detection would be required alongside something like setElementRotation and setElementVelocity to account for it.  Clearly this is not ideal.

Conclusion
==========

Analog input is something that needs to happen in order to provide proper functionality for gamemodes. Current gamemodes may suffer is no interface is provided. It also needs to be designed properly so that we dont have to worry about it come 1.01+

#### **All this has been written according to my knowledge of MTA, and feel free to correct me wherever appropriate**
