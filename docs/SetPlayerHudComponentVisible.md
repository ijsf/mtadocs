This function will show or hide a part of the player's HUD.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setPlayerHudComponentVisible ( player thePlayer, string component, bool show )
```

### Required Arguments

-   **thePlayer:** The player element for which you wish to show/hide a HUD component
-   **component:** The component you wish to show or hide. Valid values are:

:\***all:** All of the following at the same time

:\***ammo:** The display showing how much ammo the player has in their weapon

:\***area\_name:** The text that appears containing the name of the area a player has entered

:\***armour:** The display showing the player's armor

:\***breath:** The display showing the player's breath

:\***clock:** The display showing the in-game time

:\***health:** The display showing the player's health

:\***money:** The display showing how much money the player has

:\***radar:** The bottom-left corner miniradar

:\***vehicle\_name:** The text that appears containing the player's vehicle name when the player enters a vehicle

:\***weapon:** The display showing the player's weapon

-   **show:** Specify if the component should be shown (*true*) or hidden (*false*)

</section>
<section name="Client" class="client" show="true">
``` lua
bool setPlayerHudComponentVisible ( string component, bool show )
```

### Required Arguments

-   **component:** The component you wish to show or hide. Valid values are:

:\***all:** All of the following at the same time

:\***ammo:** The display showing how much ammo the player has in their weapon

:\***area\_name:** The text that appears containing the name of the area a player has entered

:\***armour:** The display showing the player's armor

:\***breath:** The display showing the player's breath

:\***clock:** The display showing the in-game time

:\***health:** The display showing the player's health

:\***money:** The display showing how much money the player has

:\***radar:** The bottom-left corner miniradar

:\***vehicle\_name:** The text that appears containing the player's vehicle name when the player enters a vehicle

:\***weapon:** The display showing the player's weapon

-   **show:** Specify if the component should be shown (*true*) or hidden (*false*)

</section>
### Returns

Returns *true* if the component was shown or hidden succesfully, *false* if an invalid argument was specified.

Requirements
------------

Example
-------

<section name="Server" class="server" show="true">
This example hides the ammo and weapon displays for players when they join.

``` lua
-- Hide some of the hud components when a player joins the server
addEventHandler ( "onPlayerJoin", root, 
    function ()
        setPlayerHudComponentVisible ( source, "ammo", false )    -- Hide the ammo displays for the newly joined player
        setPlayerHudComponentVisible ( source, "weapon", false )  -- Hide the weapon displays for the newly joined player
    end
)
```

</section>
<section name="Client" class="client" show="true">
This example hides the ammo and weapon displays for players when they join.

``` lua
-- Hide the hud when the resource is started
local components = { "weapon", "ammo", "health", "clock", "money", "breath", "armour", "wanted" }

addEventHandler("onClientResourceStart", getResourceRootElement(getThisResource()),
function ()
    for _, component in ipairs( components ) do
        setPlayerHudComponentVisible( component, false )
    end
end)
```

</section>
See Also
--------
