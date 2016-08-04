Changes the voice of a ped.

Syntax
------

``` lua
bool setPedVoice ( ped thePed, string voiceType, string voiceName )
```

### Required Arguments

-   **thePed:** the ped whose voice to change.
-   **voiceType:** the voice type. See [ped voices](/ped_voices.md "wikilink") for possible types.
-   **voiceName:** the voice name within the specified type. See [ped voices](/ped_voices.md "wikilink") for possible voices.

### Returns

Returns *true* when the voice was successfully set, *false* otherwise.

### Example

``` lua
addEventHandler("onClientResourceStart", getResourceRootElement(),
    function()
        setPedVoice(getLocalPlayer(), "PED_TYPE_GANG", "VOICE_GNG_MACCER")
    end
)
```

See Also
--------
