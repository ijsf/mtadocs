This function returns the currently selected tab in the specified [tab panel](/Element/GUI/Tab_panel.md "wikilink").

Syntax
------

``` lua
element guiGetSelectedTab ( element tabPanel )
```

### Required Arguments

-   **tabPanel:** The [tab panel](/Element/GUI/Tab_panel.md "wikilink") which current tab you want to retrieve.

### Returns

Returns an [element](/element.md "wikilink") of the [tab](/Element/GUI/Tab.md "wikilink") if a tab was selected or [nil](/nil.md "wikilink") if no tab was selected. If passed arguments were invalid or something went wrong, the function will return *false*.

Example
-------

This example gets the current selected tab and sets the selected tab to the next available tab.

``` lua
local tabPanel = guiCreateTabPanel ( 0, 0.1, 1, 1, true) --create a tab panel which fills the whole window
local tab1 = guiCreateTab("Welcome",tabPanel) --create a tab for the tab panel above
local tab2 = guiCreateTab("Info",tabPanel)--create another tab for the tab panel at the top

function check()
   if(guiGetSelectedTab(tabPanel)==tab1)then --Check what tab is currently shown
      guiSetSelectedTab(tabPanel,tab2) --if the "Welcome" tab is selected, change it to tab2("Info" tab)
   else
      guiSetSelectedTab(tabPanel,tab1) --if the "Info" tab is selected, change it to tab1("Welcome" tab)
   end
end
```

See Also
--------
