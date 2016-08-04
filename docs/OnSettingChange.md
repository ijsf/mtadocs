This event is triggered when resource setting has been changed. For instance, this event would trigger if you would edit the settings of the Race resource through the Admin panel.

Parameters
----------

``` lua
string setting, string oldValue, string newValue
```

-   **setting**: The setting which was changed. For instance: "\*race.ghostmode"
-   **oldValue**: The previous value. Please note that this value is in [JSON](/docs/JSON.md "wikilink"). To get a normal Lua value, use [fromJSON](/fromJSON.md "wikilink")
-   **newValue**: The new value. Also in [JSON](/docs/JSON.md "wikilink")

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [root element](/root_element.md "wikilink").

Example
-------

``` lua
function makeSettingsChangesVisible ( setting, oldValue, newValue )
whatItWas = fromJSON ( oldValue )
whatItsNow = fromJSON ( newValue )
outputDebugString ( "The setting "..setting.." was "..whatItWas.." and has been changed to "..whatItsNow.."." ) --Making the setting change visible in debug (use /debugscript [number] to see it)
end

addEventHandler( "onSettingChange", getRootElement(), makeSettingsChangesVisible ) --adding the event
```
