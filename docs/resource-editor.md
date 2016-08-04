The MTA:SA map editor allows you to create maps for gamemodes.

Starting
--------

To start the editor, simply click the “Map editor” menu item in the main MTA menu.

Menus
-----

Once the editor has started, you are presented with two menu bars: the main menu at the top, and the element menu in the lower left.

### Main menu

These are the buttons in the main menu:

-   ![Editor\_New.png](/images/editor_new.png) Create a new map.
-   ![Editor\_Open.png](/images/editor_open.png) Open an existing map.
-   ![Editor\_Save.png](/images/editor_save.png) Save the map you're working on.
-   ![Editor\_Save\_as.png](/images/editor_save_as.png) Save your map under a different name.
-   ![Editor\_Options.png](/images/editor_options.png) Alter general map editor settings.
-   ![Editor\_Undo.png](/images/editor_undo.png) Undo the last action.
-   ![Editor\_Redo.png](/images/editor_redo.png) Restore the last undone action.
-   ![Editor\_Locations.png](/images/editor_locations.png) Stored game world locations. The editor comes with a great list of San Andreas Interior locations but you can also add your own interior and non-interior locations to the list.
-   ![Editor\_Current\_elements.png](/images/editor_current_elements.png) List all the elements the map contains (objects, vehicles, markers, pickups etc.)
-   ![Editor\_Map\_settings.png](/images/editor_map_settings.png) Map specific settings, like time of day, gravity etc. Here you can also specify what gamemodes the map is compatible with.
-   ![Editor\_Definitions.png](/docs/images/editor_definitions.png) load [editor definition files (edf)](/resource-editor/edf.md "wikilink") that you want to use.
-   ![Editor\_Test.png](/images/editor_test.png) Go into play mode to try out the map. This will load up the gamemode the map is made for.

### Element menu

The element menu is used to add new elements to the map.

-   ![Editor\_Vehicle.png](/images/editor_vehicle.png) Create a new vehicle.
-   ![Editor\_Object.png](/images/editor_object.png) Create a new object (buildings, roads and other scenery).
-   ![Editor\_Pickup.png](/images/editor_pickup.png) Create a new pickup (health, armor, weapons and custom).
-   ![Editor\_Marker.png](/images/editor_marker.png) Create a new marker (checkpoint, ring, cylinder, arrow and corona).
-   [<File:Crosshair.png>‎](/docs/file-crosshair.png‎.md "wikilink") Select world object.

Additionally, if you have [editor definitions loaded](/docs/resource-editor/edf.md "wikilink"), you can roll the mousewheel in this menu to bring up custom elements.

Using the editor
----------------

This section explains how to create and modify maps.

### Moving around the map

When you initially start the editor, you are in *camera mode*. You are able to use the **WSAD** keys to move the camera and the mouse to pan the camera. While moving around, you can hold **ALT** to move more slowly or **SHIFT** to go faster.

To access the editor's interface and control panel you need to switch to *cursor mode*. You can toggle between cursor mode and camera mode with the **F** key. When in cursor mode, your view is fixed, and you can use the mouse cursor to manipulate elements and use the graphical interface.

Camera mode can be recognized by a crosshair in the center of the screen. You can use it to select and move elements just like in cursor mode.

[center](/docs/image-editor_crosshair.png.md "wikilink")

### Starting a new map

-   Start the editor, or if it is already started, click the *New* menu button.
-   Click the *Map settings* button. In the *Meta* tab, fill in the Name and Author fields with the name of the map and your name respectively. Also open the *Gamemodes* tab and add the gamemodes your map is meant for (they will be moved to the *Added gamemodes* list). You can do this by selecting them and clicking *Add*, or by double clicking them. Click OK when you're done.

[center](/docs/image-editor_mapsettings.png.md "wikilink")

-   Click the *Definitions* window and add the resources of which you want to use the custom elements. These will consist of the gamemodes you selected in the *Map settings* window, plus eventual additional resources. For more information about editor definitions, see [EDF](/docs/resource-editor/edf.md "wikilink"). Click OK when you're done.

### Creating new elements

Adding elements to your map, such as vehicles and objects, is very straightforward.

-   If you are in camera mode, switch to cursor mode first by pressing **F**.
-   Click the button in the element menu that represents what you want. E.g., click the button with a car on it to add a vehicle.
-   A new element of the selected type will be created and attached to your cursor. Move it to the location where you want it and **left click** to drop it off.

[center](/docs/image-editor_addelem.png.md "wikilink")

To create custom elements that are specific to a resource, hover the cursor over the element menu and turn the scroll wheel until the desired resource comes up. Note that for this to work, you first have to add the [EDF](/docs/resource-editor/edf.md "wikilink") file of the resource in the *Definitions* window.

[center](/docs/image-editor_selectedf.png.md "wikilink")

### Selecting

-   **Left click** an element to select it in *keyboard mode*.
-   **Right click** it to select it in *mouse mode*.
-   Press the **Spacebar** or click in an empty area to deselect.

The selected element, if any, is denoted by a yellow cone marker. Elements (particularly objects) with poor collisions can be detected easier by enabling *High sensitivity mode*, by pressing the **E** key. This increases detection at the expense of accuracy.

The *Current elements* dialog can also be used to select elements. Double-clicking an item within the list will select it in *Keyboard mode*.

### Moving

Moving elements can be done in several ways.

**With the mouse**

-   Simply drag and drop with the **left mouse button**.

Or:

-   Select the element in mouse mode (**right click**), move it to where you want it, and click to drop it off.

You can also adjust the *Hold distance* of an element toward and away from the camera by switching to camera mode, **right clicking** the element, and rolling the **mouse wheel**.

**With the keyboard**

-   Select the element in keyboard mode (**left click**).
-   Use the **arrow keys** to move the element in the horizontal plane, and **PgUp**/**PgDn** to move it vertically. Hold **ALT** to decrease the movement speed, or **SHIFT** to increase it.

By default, elements move relative to the camera and are not locked to any axes. This can be disabled in the *Options* menu.

### Rotating

**With the mouse**

You can rotate selected elements around the Z axis with the mouse wheel.

-   Select the element in keyboard mode (**left click**) and roll the mouse wheel while holding **Left CTRL**.

Or:

-   Select the element in mouse mode (**right click**), hold **CTRL**, and roll the mouse wheel.

**With the keyboard**

-   Select the element in keyboard mode (**left click**).
-   While holding **CTRL** (the selection marker will turn green), use the **arrow keys** and **PgUp**/**PgDn** to rotate the element around the different axes.

With both methods you can additionally hold **ALT** to decrease the rotation speed or **SHIFT** to increase it.

[center](/docs/image-editor_rotateelem.png.md "wikilink")

### Changing model and other properties

Most elements have a variety of options that can be altered to change their appearance and behaviour. Examples are the model, color and visual upgrades of a car.

-   Open the properties window of an element by either double clicking it or by selecting it and pressing **F3**.
-   Make any alterations that you want. For example, to change the model of a car or object, click the **Browse** button next to “model” to open the model browser.
-   Click OK when you're done.

[center](/docs/image-editor_props.png.md "wikilink")

### Cloning

You can clone an element by selecting it and pressing **C**.

-   In mouse mode the cloned element will be attached to your cursor. **Left click** to place it in the map.
-   In keyboard mode the cloned element will be cloned in the identical position.

If you hold **CTRL** while clicking, the element will be cloned again and will again be attached to the cursor. This way you can easily place large quantities of something.

Alternatively you can use the *Pullout* button located in the bottom-right corner of the properties box to clone an element.

### Deleting

Simply select the element and press **DEL** *(Delete)*.

Alternatively you can use the *Pullout* button located in the bottom-right corner of the properties box to delete an element.

Creating maps for specific gamemodes
------------------------------------

To make a map for a specific gamemode, you have to do two things:

-   Click the **Map Settings** button in the top menu, go to the **Gamemodes** tab and add any gamemodes that your map is to be used with.
-   You will likely also need to add one or more [Editor Definition Files](/docs/resource-editor/edf.md "wikilink"). These will allow you to place gamemode specific elements in the map, like spawnpoints, race checkpoints, or CTF flags. You can add EDF's by clicking the **Definitions** menu button and adding the relevant gamemodes.

Controls
--------

Here is a list of all default controls. To change them please go to the MTA Settings menu while the Editor is started.

### Camera

|                         |       |
|-------------------------|-------|
| camera\_move\_forwards  | **w** |
| camera\_move\_backwards | **s** |
| camera\_move\_left      | **a** |
| camera\_move\_right     | **d** |
| high\_sensitivity\_mode | **e** |

### Cloning

|                          |           |
|--------------------------|-----------|
| clone\_selected\_element | **c**     |
| clone\_drop\_modifier    | **lctrl** |

### Element manipulation

|                            |                                          |                                  |
|----------------------------|------------------------------------------|----------------------------------|
| element\_move\_forward     | **arrow\_u**                             | *(Arrow key Up)*                 |
| element\_move\_backward    | **arrow\_d**                             | *(Arrow key Down)*               |
| element\_move\_left        | **arrow\_l**                             | *(Arrow key Left)*               |
| element\_move\_right       | **arrow\_r**                             | *(Arrow key Right)*              |
| element\_move\_downwards   | **pgdn**                                 | *(Page Down)*                    |
| element\_move\_upwards     | **pgup**                                 | *(Page Up)*                      |
| zoom\_in                   | **mouse\_wheel\_down**                   |
| zoom\_out                  | **mouse\_wheel\_up**                     |
| quick\_rotate\_increase    | **mod\_rotate** + **mouse\_wheel\_up**   | *(Left CTRL + Mouse wheel Up)*   |
| quick\_rotate\_decrease    | **mod\_rotate** + **mouse\_wheel\_down** | *(Left CTRL + Mouse wheel Down)* |
| mod\_rotate                | **lctrl**                                | *(Left CTRL)*                    |
| mod\_slow\_speed           | **lalt**                                 | *(Left ALT)*                     |
| mod\_fast\_speed           | **lshift**                               | *(Left SHIFT)*                   |
| destroy\_selected\_element | **delete**                               |
| drop\_selected\_element    | **space**                                |
| pickup\_selected\_element  | **F2**                                   |
| reset\_rotation            | **mod\_rotate** + **r**                  | *(Left CTRL + R)*                |

### GUI

|                          |                        |
|--------------------------|------------------------|
| toggle\_gui\_display     | **F4**                 |
| toggle\_cursor           | **f**                  |
| select\_target\_keyboard | **mouse1**             |
| select\_target\_mouse    | **mouse2**             |
| edf\_next                | **mouse\_wheel\_up**   |
| edf\_prev                | **mouse\_wheel\_down** |
| undo                     | **Ctrl** + **z**       |
| redo                     | **Ctrl** + **y**       |
| properties\_toggle       | **F3**                 |
| browser\_up              | **arrow\_u**           |
| browser\_down            | **arrow\_d**           |
| browser\_zoom\_in        | **mouse\_wheel\_up**   |
| browser\_zoom\_out       | **mouse\_wheel\_down** |
| browser\_confirm         | **enter**              |
| currentelements\_up      | **num\_8**             |
| currentelements\_down    | **num\_2**             |
| toggle\_test             | **F5**                 |

Multiplayer
-----------

The editor is built with both serverside and clientside components, and therefore supports multiplayer out of the box. To use the editor in multiplayer with other players, simply copy all of the editor's resources into your server, start the **editor** resource and allow other players to join.

Please note that currently the editor lacks any permissions system, so all users have access to every function.

Plugins & External resources
----------------------------

The editor allows basic importing of elements from external resources. This is useful for resources that may have to manipulate an element in a specific way that cannot be performed by the editor. For example, a map resource which uses custom models (and has a script to import these models) cannot be manipulated by default within the editor.

By using the **import <resourceName>** command in console the resource's elements can be imported within the editor.

FAQ
---

#### I get a black screen when launching the Map Editor

Usually this is caused due to incorrect installation of Map Editor resources. If you are using a stable MTASA client, please install it again and make sure that you use Client and Server install option.

If you are using a nightly build, to get it working right you need to download latest [resources (step 3)](http://code.google.com/p/multitheftauto/wiki/NightlyBuilds?tm=2), unpack the archive and put its contents in: *MTA San Andreas\\server\\mods\\deathmatch\\resources* , where *MTA San Andreas* is a folder where you've installed MTA San Andreas (default location: C:\\Program Files\\MTA San Andreas).

Putting them in this path: MTA San Andreas\\mods\\deathmatch\\resources **is a common mistake** - it won't work if you put them there. So make sure to put them in the *italic* path above.

If this issue still occurs, even when you've checked the note above and verified that you've installed it correctly, it might be because you've got an outdated **acl.xml** file. You can download the default one [here](http://multitheftauto.googlecode.com/svn/trunk/MTA10_Server/mods/deathmatch/acl.xml). It should be placed in **server/mods/deathmatch/** in your MTA: San Andreas installation directory.

#### I get an “Could not start the local server. See console for details” when using the “Map Editor” button

This is because you do not have a valid editor.conf installed. You can download the default one [here](http://multitheftauto.googlecode.com/svn/trunk/MTA10_Server/mods/deathmatch/editor.conf). It should be placed in **server/mods/deathmatch/** in your MTA: San Andreas installation directory.

#### I have saved a map but cannot find it in my server's resources directory, despite the Editor itself being able to see it

This is due to the fact that Vista/7 limits write-access for non-admin processes in Program Files directory. Files get written in the “VirtualStore” directory instead of real Program Files folder. You should be able to locate your map resource in a similar directory to:

`C:\Users\`<USERNAME>`\AppData\Local\VirtualStore\Program Files\MTA San Andreas\server\mods\deathmatch\resources\`

Running the Server/MTA San Andreas with Administrative rights will allow the map to be saved to the proper location.

#### I have some other problem with the map editor

Sometimes resetting the map editor will solve certain issues. The easiest way to do that is install MTA:SA to a brand new folder. Otherwise you can try the following steps:

  
  
1. Go to the resources folder, **server/mods/deathmatch/resources/** and delete the **editor\_dump** directory

2. Go to the resources folder, **server/mods/deathmatch/resources/** and delete the **editor\_test** directory

#### I have found a bug or have a suggestion/feedback for the map editor

Please use the official [bugtracker](http://bugs.mtasa.com) for reporting bugs. Feel free to also join us on [IRC](http://www.multitheftauto.com/irc.html).

[ru:<Resource:Editor>](/docs/ru-resource-editor.md "wikilink") [es:<Resource:Editor>](/docs/es-resource-editor.md "wikilink")
