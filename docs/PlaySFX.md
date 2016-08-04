Syntax
------

``` lua
element playSFX ( string containerName, int bankId, int soundId [, bool looped = false ] )
```

### Required Arguments

-   **containerName:** The name of the audio container. Possible values are: “feet”, “genrl”, “pain\_a”, “script”, “spc\_ea”, “spc\_fa”, “spc\_ga”, spc\_na", “spc\_pa”
-   **bankId:** The audio bank id
-   **soundId:** The sound id within the audio bank

### Optional Arguments

-   **looped:** A [boolean](/boolean.md "wikilink") representing whether the sound will be looped

Returns
-------

Returns a [sound](/sound.md "wikilink") element if the sound was successfully created, *false* otherwise.

Example
-------

The following example plays a firealarm sound (looped).

``` lua
if not playSFX("script", 7, 1, true) then
    outputChatBox("You have to install some missing audio files to hear the sound")
end
```

See Also
--------
