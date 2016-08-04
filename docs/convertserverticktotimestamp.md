This function converts server ticks to a unix timestamp. **Note**: this was built to work with the server tick timestamp returned by [onPlayerScreenShot](/docs/onplayerscreenshot.md "wikilink"). Author: qaisjp

Syntax
------

``` lua
int convertServerTickToTimeStamp( int ticks )
```

### Required Arguments

-   **ticks**: The ticks to be converted. **REMEMBER:** the input tick cannot be from a different server session, this is because ticks are “reset” when the server is booted.

### Returns

Returns an int containing the unix timestamp number.

Code
----

``` lua
function convertServerTickToTimeStamp(tick) return getRealTime().timestamp+((getTickCount()*0.001)-(tick*0.001)); end
```

See Also
--------
