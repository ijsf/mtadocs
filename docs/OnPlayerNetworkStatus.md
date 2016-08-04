Parameters
----------

``` lua
int status, int ticks
```

-   **status**: A number which is 0 if the interruption has begun, or 1 if the interruption is ending.
-   **ticks**: Number of ticks since the interruption started.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that has the network interruption.

Example
-------

This example shows a debug message when interruption starts and stops.

``` lua
addEventHandler( "onPlayerNetworkStatus", root,
  function( status, ticks )
    if status == 0 then
      outputDebugString( "(packets from " .. getPlayerName(source) .. ") interruption began " .. ticks .. " ticks ago" )
    elseif status == 1 then
      outputDebugString( "(packets from " .. getPlayerName(source) .. ") interruption began " .. ticks .. " ticks ago and has just ended" )
    end
  end
)
```

See Also
--------

### Other events
