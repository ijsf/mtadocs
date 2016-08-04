Syntax
------

``` lua
element playSFX3D ( string containerName, int bankId, int soundId, float x, float y, float z [, bool looped = false ] )
```

### Required Arguments

-   **containerName:** The name of the audio container. Possible values are: “feet”, “genrl”, “pain\_a”, “script”, “spc\_ea”, “spc\_fa”, “spc\_ga”, spc\_na", “spc\_pa”
-   **bankId:** The audio bank id
-   **soundId:** The sound id within the audio bank
-   **x:** A floating point number representing the X coordinate on the map.
-   **y:** A floating point number representing the Y coordinate on the map.
-   **z:** A floating point number representing the Z coordinate on the map.

### Optional Arguments

-   **looped:** A [boolean](/docs/boolean.md "wikilink") representing whether the sound will be looped

Returns
-------

Returns a [sound](/docs/sound.md "wikilink") element if the sound was successfully created, *false* otherwise.

Example
-------

The following example plays a fire alarm sound near you (looped).

``` lua
local x, y, z = getElementPosition(localPlayer)
if not playSFX3D("script", 7, 1, x + 10, y, z, true) then
    outputChatBox("You have to install some missing audio files to hear the sound")
end
```

See Also
--------
