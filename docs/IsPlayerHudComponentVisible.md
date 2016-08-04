This function can be used to check whether an hud component is visable or not.

Syntax
------

``` lua
bool isPlayerHudComponentVisible( string component )
```

### Required Arguments

-   **component:** The component you wish to check. Valid values are:

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

### Returns

Returns *true* if the component is visable, *false* if not.

Example
-------

``` lua
addEventHandler("onClientResourceStart",resourceRoot,function()
    local components = {"ammo","area_name","armour","breath","clock","health","money",
        "radar","vehicle_name","weapon","radio","wanted","crosshair"
    } --Table filled with all the available components to check
    for _,component in ipairs(components)do
        if isPlayerHudComponentVisible(component)then --check if the component is visible
            outputChatBox("Hud Component: "..component.." is visible!") --if it is then tell the client that
        else
            outputChatBox("Hud Component: "..component.." is not visible!") --if it is not then tell the client that it isn't
        end
    end
end)
```

Requirements
------------

See Also
--------
