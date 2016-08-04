Syntax
------

``` lua
bool getSFXStatus ( string audioContainer )
```

### Required Arguments

-   **audioContainer:** The container name. Possible values are: “feet”, “genrl”, “pain\_a”, “script”, “spc\_ea”, “spc\_fa”, “spc\_ga”, spc\_na", “spc\_pa”

Returns
-------

Returns *true* if the sound container is available, *false* otherwise.

Example
-------

``` lua
if not getSFXStatus("spc_ea") then
   outputChatBox("Please install the missing audio files to enjoy the full gaming experience")
end
```

See Also
--------
