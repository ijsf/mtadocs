This event triggers when raw data is sent from the IRC server to the module. Thanks to this, scripts can know when something has happened on IRC. (i.e. chatting)

Parameters
----------

``` lua
string content
```

-   **content**: The raw command that has been sent to the module

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [root element](/root_element.md "wikilink").

Example
-------

``` lua
local root = getRootElement()

function handleRawIRCData(msg)
  if msg then
    outputServerLog(msg) -- Shows all incoming IRC data as a string
  end
end
addEventHandler("onIRCRaw", root, handleRawIRCData)
```

See also
--------
