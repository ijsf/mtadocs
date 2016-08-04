This page lists all the control names. These can be used as key arguments by the console commands *bind* and *unbind* as well as the script functions [bindKey](/docs/bindkey.md "wikilink"), [unbindKey](/docs/unbindkey.md "wikilink") etc.

Lua table of all the valid control names listed on this page:

``` lua
controlTable = { "fire", "next_weapon", "previous_weapon", "forwards", "backwards", "left", "right", "zoom_in", "zoom_out",
 "change_camera", "jump", "sprint", "look_behind", "crouch", "action", "walk", "aim_weapon", "conversation_yes", "conversation_no",
 "group_control_forwards", "group_control_back", "enter_exit", "vehicle_fire", "vehicle_secondary_fire", "vehicle_left", "vehicle_right",
 "steer_forward", "steer_back", "accelerate", "brake_reverse", "radio_next", "radio_previous", "radio_user_track_skip", "horn", "sub_mission",
 "handbrake", "vehicle_look_left", "vehicle_look_right", "vehicle_look_behind", "vehicle_mouse_look", "special_control_left", "special_control_right",
 "special_control_down", "special_control_up" }
```

GTA control list
----------------

<div style="border:3px solid green;margin-bottom:3px;">
<div style="float:right;padding-right:5px;font-weight:bold;">
ON FOOT

</div>
-   **fire** Fire a player's weapon
-   **next\_weapon** Switch to the next weapon
-   **previous\_weapon** Switch to the previous weapon
-   **forwards** Move forwards
-   **backwards** Move backwards
-   **left** Move left
-   **right** Move right
-   **zoom\_in** Zoom targeted weapon in (sniper/rocket launcher/camera etc)
-   **zoom\_out** Zoom targeted weapon out
-   **change\_camera** Change camera mode
-   **jump** Make the player jump
-   **sprint** Make the player sprint
-   **look\_behind** Make the player look behind (and allow the player to see behind them)
-   **crouch** Make the player crouch/duck
-   **action** Show the stats menu
-   **walk** Make the player move slowly/quietly
-   **aim\_weapon** Aim the player's current weapon (if possible)
-   **conversation\_yes** Answer yes to a question
-   **conversation\_no** Answer no to a question
-   **group\_control\_forwards** Make the group you are controlling move forwards
-   **group\_control\_back** Make the group you are controlling move backwards
-   **enter\_exit** Make the player enter a vehicle. Also used for alternative fighting styles.

</div>
<div style="border:3px solid red;margin-bottom:3px;">
<div style="float:right;padding-right:5px;font-weight:bold;">
IN VEHICLE

</div>
-   **vehicle\_fire** Fire the player's vehicle's primary weapon (e.g. hunter's missiles) or shoot with driveby
-   **vehicle\_secondary\_fire** Fire the player's vehicle's secondary weapon (e.g. hunter's minigun)
-   **vehicle\_left** Make the player's vehicle turn left
-   **vehicle\_right** Make the player's vehicle turn right
-   **steer\_forward** Make the player's vehicle turn down (lean forwards for helicopters/planes)
-   **steer\_back** Make the player's vehicle turn up (lean backwards for helicopters/planes)
-   **accelerate** Make the player's vehicle accelerate
-   **brake\_reverse** Make the player's vehicle brake (slow down) and if stationary reverse
-   **radio\_next** Change to the next radio station (Doesn't work - use [setRadioChannel](/docs/setradiochannel.md "wikilink") and [onClientPlayerRadioSwitch](/docs/onclientplayerradioswitch.md "wikilink") instead.)
-   **radio\_previous** Change to the previous radio station (Doesn't work - use [setRadioChannel](/docs/setradiochannel.md "wikilink") and [onClientPlayerRadioSwitch](/docs/onclientplayerradioswitch.md "wikilink") instead.)
-   **radio\_user\_track\_skip** Skip the current track being played on the custom radio station
-   **horn** Play the horn of the player's vehicle (if the vehicle has a horn) and can trigger the siren on emergency vehicles
-   **sub\_mission** Start a submission if one is avaliable (e.g. taxi missions)
-   **handbrake** Apply the handbrake on the player's vehicle
-   **vehicle\_look\_left** Look to the left
-   **vehicle\_look\_right** Look to the right
-   **vehicle\_look\_behind** Look behind
-   **vehicle\_mouse\_look**
-   **special\_control\_left** Move the some special vehicle component left (e.g. tank's turret)
-   **special\_control\_right** Move the some special vehicle component right (e.g. tank's turret)
-   **special\_control\_down** Move the some special vehicle component down (e.g. tank's turret)
-   **special\_control\_up** Move the some special vehicle component up (e.g. tank's turret)
-   **enter\_exit** Make the player exit a vehicle

</div>
MTA hard-coded commands
-----------------------

The following are names of hard-coded MTA commands which do not use bindKey, but can act as bindKey by using them in an [addCommandHandler](/docs/addcommandhandler.md "wikilink"). Other than that, this control list will **only** work with the functions [toggleControl](/docs/togglecontrol.md "wikilink") and [toggleAllControls](/docs/toggleallcontrols.md "wikilink"). Please note that [toggleControl](/docs/togglecontrol.md "wikilink") can't disable screenshot.

<div style="border:3px solid blue;margin-bottom:3px;">
<div
style="float:right;padding-right:5px;font-weight:bold;">
MTA COMMANDS

</div>
-   **enter\_passenger** Enters the closest vehicle as passenger
-   **screenshot** Takes a screenshot
-   **chatbox** Opens the chatbox for input
-   **radar** Toggles the radar-map showing
-   **radar\_zoom\_in** Zooms in on the radar-map
-   **radar\_zoom\_out** Zooms out on the radar-map
-   **radar\_move\_north** Moves north on the radar-map
-   **radar\_move\_south** Moves south on the radar-map
-   **radar\_move\_east** Moves east on the radar-map
-   **radar\_move\_west** Moves west on the radar-map
-   **radar\_attach** Attaches the view to the local-player on the radar-map

</div>
[Category:Scripting Concepts](/docs/category-scripting_concepts.md "wikilink")
