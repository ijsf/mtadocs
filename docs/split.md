This function splits a string into substrings. You specify a character that will act as a separating character; this will determine where to split the sub-strings. For example, it can split the string “Hello World” into two strings containing the two words, by spliting using a space as a separator.

**Note:** You can use the function [gettok](/docs/gettok.md "wikilink") to retrieve a single token from the string at a specific index. This may be faster for one-off lookups, but considerably slower if you are going to check each token in a long string.

Syntax
------

``` lua
table split ( string stringToSplit, string / int separatingChar )
```

### Required Arguments

-   **stringToSplit** The string you wish to split into parts.
-   **separatingChar** A string of the character you want to split, or the [ASCII number](/docs/ASCII.md "wikilink") representing the character you want to use to split.

### Returns

Returns a *table* of substrings split from the original string if successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example gives the specified weapons to the given player, while the weapons are a string in the form: 'weaponId,ammo;weaponId2,ammo2;weaponId3,ammo3;..'. This is especially for data read from a .map file attribute.

``` lua
function giveWeapons(player, weaponsString)
    local weaponsTable = split(weaponsString, ';') --split the string by the semi colon
    for k,v in ipairs(weaponsTable) do --for all the split values do
        weaponId = gettok(v, 1, string.byte(',')) --get the weapon ID using gettok, retrieve the first token
        weaponAmmo = gettok(v, 2, string.byte(',')) --get the ammo using gettok, retrieve the second token
        if (weaponId ~= nil and weaponAmmo ~= nil) then --if neither of them is invalid
            giveWeapon(player, weaponId, weaponAmmo) --give the player the weapons
        end
    end
end
```

</section>
See Also
--------
