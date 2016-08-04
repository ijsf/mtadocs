This event is triggered each time the user switch from GUI tab.

Parameters
----------

``` lua
element theElement
```

-   **theElement**: The tab which was selected.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the tab.

Example
-------

This example creates a window with a tabpanel with two tabs. Every time a user changes tabpage a notification will be shown.

First we'll create the window. Then add a tabpanel and couple tabs with some labels in them. Qoute: [GuiCreateWindow\#Example](/docs/GuiCreateWindow#Example.md "wikilink")

``` lua
local myWindow = guiCreateWindow ( 0, 0, 0.5, 0.4, "Information", true )  -- create a window which has "Information" in the title bar.
local tabPanel = guiCreateTabPanel ( 0, 0.1, 1, 1, true, myWindow )       -- create a tab panel which fills the whole window
local tabMap = guiCreateTab( "Map Information", tabPanel )                -- create a tab named "Map Information" on 'tabPanel'
local tabHelp = guiCreateTab( "Help", tabPanel )                          -- create another tab named "Help" on 'tabPanel'
 
-- adds a label (text) to each tab
guiCreateLabel( 0.02, 0.04, 0.94, 0.2, "This is information about the current map", true, tabMap )
guiCreateLabel( 0.02, 0.04, 0.94, 0.92, "This is help text.", true, tabHelp )
```

Now let's add the event handler.

``` lua

function OnChange(selectedTab)
    -- If there is a selected tab.
    if selectedTab ~= nil then 
        outputChatBox( "You've changed your active tab." )
    end 
end

addEventHandler("onClientGUITabSwitched", root, OnChange)
```

See Also
--------

### GUI events

### Client event functions
