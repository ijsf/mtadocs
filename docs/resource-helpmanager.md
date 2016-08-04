The help manager centralizes script help GUIs and provides a simple way to add instructions. Users can be notified with a popup the first time a resource's help page is loaded.

Usage
-----

### Simple GUI

If you just want to add a text, adding this **exact** (don't change src nor type) line to your meta.xml will be enough:

``` xml
<config src="help.xml" type="client"/>
```

The contents below the root node of your **help.xml** file will be shown under the resource's help tab. Also, an optional popup=“no” can be added to the root node to specify that you don't want the user to be notified with a popup when the page is available.

For example:

``` xml
<help popup="no">
Help text here
</help>
```

Help text should explain how to play the gamemode, bound keys and console commands. The help is intended for the end user, not the developer so keep it simple.

### Custom GUI

You can add your custom help GUI by adding the tab manually in a client script:

``` lua
myHelpTab = call(getResourceFromName("helpmanager"), "addHelpTab", getThisResource(), true)
```

You can add contents by using the returned GUI element as GUI parent for your widgets. It is not necessary to destroy them on page remove / resource stop, as the manager does cleanup.

Keys
----

**F9**: toggles the help window.

Commands
--------

**gamehelp**: toggles the help window.

Exported functions
------------------

### Server

``` lua
bool showHelp ( element showTo )
```

Shows the help window for the showTo element, propagating down the tree.

``` lua
bool hideHelp ( element hideTo )
```

Hides the help window for the hideTo element, propagating down the tree.

### Client

``` lua
bool showHelp ()
```

Shows the help window for the local player.

``` lua
bool hideHelp ()
```

Hides the help window for the local player.

``` lua
 )
```

Adds a gui-tab with the name of the passed resource to the local player's help GUI. If showPopup is false, the “page available” popup is not shown.

``` lua
bool removeHelpTab ( resource forResource )
```

Adds a gui-tab with the name of the passed resource to the local player's help GUI.

Fired events
------------

### Client

*(For all events, “source” is the local player.)*

``` lua
onHelpShown ()
```

``` lua
onHelpHidden ()
```

[ru:<Resource:Helpmanager>](/docs/ru:resource:helpmanager.md "wikilink")
