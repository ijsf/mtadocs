Introduction
------------

The editor provides functions and commands to interface with external resources. Normally creating elements or any such actions outside the editor makes them unseeable or unmanipulatable. By importing elements, the editor is made to be compatible and is able to manipulate them, and save them into its map resource. In practice, this allows basic development of plugins, or allowing manual compatibility to external resources.

Commands
--------

An “import” command is exported in order to allow users to import the elements of a specified resource:

``` lua
import <resourceName>
```

-   **resourceName:** The name of the resource you wish to import from.

The elements from the resource will then be imported. A practical use is for the importing of custom models. While the editor is unable to load custom models itself, by importing models from a resource which can, a custom map can be created. For example, the following steps could be performed in order order to modify custom map sth-aztec

-   Start the editor
-   Start (Not Open) sth-aztec manually. This will start the map and load the custom models.
-   Type “import sth-aztec” and the objects will be imported into the editor
-   The map will now be loaded

Functions
---------

The **editor** resource also exports an *import* function. This replicates the command, but also allows importing element datatypes. Essentially this allows resources to have control over importing without having to have permission from the editor itself..

``` lua
bool import ( element rootElement/resource resourceToImportFrom )
```

-   **rootElement:** The root element of which you wish to import (The root itself and all children will be imported)

**OR:**

-   **resourceToImportFrom:** The resource pointer of which you wish to import.

Editor plugins
--------------

#### Editor Loop Generator

[thumb|Loop generator working with the editor.|400x250px](/docs/image:loopgenerator.jpg.md "wikilink") An example use for this is the loop generator plugin, adapted from Offroader23's work on *offedit*.

This resource adds custom gui which can be used to create perfect loops out of standard objects. After perfoming this, it uses the exported *import* function and allows the editor to manipulate them.

Download no longer available, hosted site closed.

#### Editor racemap loader

This plugin will load objects from your race maps without the need for conversion.

Download no longer available, hosted site closed.

#### Roller Coaster Generator

With this plugin, you can create easily roller coaster like maps. [Learn more by clicking here.](/docs/roller_coaster_generator.md "wikilink") [ru:<Resource:Editor/Plugins>](/ru:Resource:Editor/Plugins.md "wikilink")

#### Object Movement Generator

An attempt to help some people create moving objects (using moveObject function) more easily.

Download [here](http://community.mtasa.com/index.php?p=resources&s=details&id=1224)
