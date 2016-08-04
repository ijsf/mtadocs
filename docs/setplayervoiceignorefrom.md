<div style="border: 1px dotted blue; background: #00CC66;padding:4px;margin-bottom:2px;">
**Note**: This function should only be used as a low-level function for advanced users. For typical Voice scripting, please see the [Voice Resource](/docs/resource-voice.md "wikilink")

</div>
This function allows you to mute voices for a player.

Syntax
------

``` lua
bool setPlayerVoiceIgnoreFrom ( element thePlayer, mixed ignoreFrom )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") you wish to change
-   **ignoreFrom:** Element or table of elements which the player should not hear voices from. Use *nil* if no one should be ignored.

### Returns

Returns *true* if the value was set successfully, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">

</section>
See Also
--------
