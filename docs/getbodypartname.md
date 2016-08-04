This function is used to get the name of a body part on a player.

Syntax
------

``` lua
string getBodyPartName ( int bodyPartID )
```

### Required Arguments

-   **bodyPartID**: An integer representing the body part ID you wish to retrieve the name of.

Returns
-------

This function returns a string containing the body part name if the ID is valid, *false* otherwise.

Example
-------

This example prints the killer and body part to the chat on the wasted/kill event.

``` lua
function deathMessageOnWasted ( ammo, attacker, weapon, bodypart )
  if ( attacker ) then                                    -- if we have an attacker
    if ( getElementType ( attacker ) == "player" ) then   -- make sure the element that killed him was a player
      tempString = getPlayerName ( attacker ) .. " killed " .. getPlayerName ( source ) .. " (" .. getWeaponNameFromID ( weapon ) .. ")"
      if ( bodypart == 9 ) then -- if he was shot in the head
        tempString = tempString .. " (HEADSHOT!)"
      else
        tempString = tempString .. " (" .. getBodyPartName ( bodypart ) .. ")"
      end
      outputChatBox ( tempString )
    else
      outputChatBox ( getPlayerName ( source ) .. " died. (" .. getWeaponNameFromID ( weapon ) .. ") (" .. getBodyPartName ( bodypart ) .. ")" )
    end
  else
    outputChatBox ( getPlayerName ( source ) .. " died. (" .. getWeaponNameFromID ( weapon ) .. ") (" .. getBodyPartName ( bodypart ) .. ")" )
  end
end
addEventHandler ( "onPlayerWasted", root, deathMessageOnWasted )
```

See Also
--------

[PL:GetBodyPartName](/docs/pl-getbodypartname.md "wikilink")
