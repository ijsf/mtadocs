This function gets the amount of ammo left in a [custom weapon](/docs/Element/Weapon.md "wikilink")'s magazine/clip.

Syntax
------

``` lua
int getWeaponClipAmmo ( weapon theWeapon )
```

### Required Arguments

-   **theWeapon:** the [weapon](/docs/weapon.md "wikilink") to get the clip ammo of.

### Returns

Returns the amount of ammo in the [custom weapon](/docs/Element/Weapon.md "wikilink")'s clip, *false* if an error occured.

### Example

This function outputs the remaining ammo in clip of a specific weapon using the command */getammoinclip*.

    [lua]
    local customWeapon

    addEventHandler( "onClientResourceStart", resourceRoot,
        function()
            local x, y, z = getElementPosition(localPlayer) -- Get player position
            customWeapon = createWeapon("m4", x, y, z + 1) -- Create a M4
            setWeaponClipAmmo(customWeapon, 99999) -- Set the ammo in clip of the weapon to 99999, so it never should reload
            setWeaponState(customWeapon, "firing") -- Fire it permanently
            -- Add the 'getammoinclip' command to get the remaining ammo in clip of the weapon
            addCommandHandler("getammoinclip", getM4WeaponAmmo)
        end
    )

    function getM4WeaponAmmo()
        if customWeapon then
            -- Tell the player the remaining ammo in clip
            outputChatBox(getWeaponClipAmmo(customWeapon))
        else
            -- Weapon was not created, give an error
            outputChatBox("There is no weapon to get clip ammo of.")
        end
    end

See also
--------
