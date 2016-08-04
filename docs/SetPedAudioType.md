Use [setPedVoice](/setPedVoice.md "wikilink") instead.

Sets a ped's audio type.

Syntax
------

``` lua
bool setPedAudioType ( ped thePed, string audio )
```

### Required Arguments

-   **thePed:** the ped whose audio type to change.
-   **audio:** the name of the audio type to set. Possible values are:
    -   PED\_TYPE\_GEN
    -   PED\_TYPE\_EMG
    -   PED\_TYPE\_PLAYER
    -   PED\_TYPE\_GANG
    -   PED\_TYPE\_GFD

### Returns

Returns *true* if the voice type was set successfully, *false* otherwise.

See Also
--------
