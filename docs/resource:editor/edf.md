EDF stands for *Editor Definition File*. EDF's are XML files with an .edf extension that describe the custom elements used by a resource: new element types that have no meaning to MTA itself. Examples are &lt;spawnpoint&gt;, &lt;flag&gt;, &lt;checkpoint&gt; etc. They also are used to define settings that are used by gamemodes, which are placed under the &lt;settings&gt; tag within a resource's *meta.xml*.

Introduction
------------

Some resources use custom map elements. A capture the flag gamemode, for example, will likely use &lt;flag&gt; elements that contain flag positions and teams. When a map is loaded, the gamemode looks for any &lt;flag&gt; elements and installs flags accordingly - for example by creating a flag object and a collision shape.

The problem with these custom elements is that, unlike built-in MTA elements, the map editor has no idea of their meaning. How should a &lt;flag&gt; element be visually represented? What properties does it have? Without telling the editor this information, you could not use it to create these custom elements and would instead have to resort to manually editing the .map file with a text editor. Fortunately this isn't necessary: any resource can contain an editor definition file that describes the custom map elements used by that resource.

Using definition files in the editor
------------------------------------

As described in the [main editor manual](/docs/resource:editor.md "wikilink"), to be able to create the custom elements of a resource in your map you need to add it in the *Definitions* window. Click the *Definitions* button in the main menu and double click the resource in the left list. Then close the window and roll the mousewheel in the element panel until the resource comes up. At that point you can create and manipulate custom elements of that resource like any other element.

Writing EDF files
-----------------

EDF files are simply XML files with an .edf extension. We'll start with an example: the EDF of the Capture the Orb gamemode.

``` xml
<def name="Capture the Orb">
    <element name="orb" friendlyname="Orb spawnpoint" instructions="Place your orb in a position that can be collected.">
        <data name="position" type="coord3d" default="0,0,0" />
        <marker size="0.5" type="corona" color="#ffff00ff" />
    </element>
    <element name="objective" friendlyname="Objective point" instructions="Place your objective point in a position that can be reached.">
        <data name="position" type="coord3d" default="0,0,0" />
        <marker size="3" type="cylinder" color="#9370dbaa" />
    </element>
    <element name="spawnpoint" friendlyname="Spawnpoint">
        <object editorOnly="true" model="3092" posZ="1" />
        <data name="position" type="coord3d" default="0,0,0" />
        <data name="rotation" type="coord3d" default="0,0,0" />
        <data name="skin" type="skinID" default="0" />
    </element>
</def>
```

As you can see, the syntax is fairly straightforward. The root element, &lt;def&gt;, contains a number of &lt;element&gt;s. Each of these &lt;element&gt;s describes a custom element and specifies its name, visual representation and available properties.

### Visual representation

Any child node of an &lt;element&gt; that is not a &lt;data&gt; node is part of the visual representation. There can be one or more objects, markers, pickups etc. For each representation element you can optionally specify a position (posX, posY, posZ) and rotation (rotX, rotY, rotZ): these are *relative* to the position and rotation of the represented custom element. Using the above Capture the Orb example, if you were to create a spawnpoint at (30, 14, 3), the editor would display an object of model 3092 at (30, 14, 4) to represent it, because the object's posZ of 1 is added to the spawnpoint's z position of 3.

### Properties

Properties of a custom element are described by &lt;data&gt; nodes. Some property names have a special meaning, like *position* and *rotation*: these can be changed by moving and rotating the element in the editor. The other properties can be changed in the Properties window.

### Property-dependent visual representation

It is possible to make the representation of a custom element depend on one or more of the element's properties. Take as example a &lt;checkpoint&gt; element of a race gamemode that contains a &lt;marker&gt; for representation: the checkpoint has several attributes like color and size that should be reflected in the marker. To accomplish this, specify something of the form *!propertyname!* in one or more of the representing element's attributes. For example:

``` xml
<def name="Race">
    <element name="checkpoint" friendlyname="Race checkpoint">
        <data name="position" type="coord3d" required="true" default="0,0,0" />

        <data name="type" type="selection:checkpoint,ring" required="true" default="checkpoint" />
        <data name="size" type="number" required="true" default="2.25"/>
        <data name="color" type="color" required="false" default="#ff0000ff" />
        ...
        
        <marker type="!type!" size="!size!" color="!color!" />
    </element>
</def>
```

Now whenever the “type”, “size” or “color” property of a checkpoint is changed, the new value will be copied to its marker, and the marker's visual appearance changes accordingly.

### Integrating in a resource

Once you've written your EDF, save it as an .edf file in your resource's folder and add an “edf:definition” attribute to your meta.xml's &lt;info&gt; tag, like so:

``` xml
<meta>
    <info author="erorr404" type="gamemode" ... edf:definition="cto.edf" />
    ...
</meta>
```

EDF reference
-------------

### Built-in elements

These are the elements you can use for representing your custom elements, along with their properties.

| &lt;blip&gt; |
|--------------|
| Property     |
| position     |
| icon         |
| size         |
| color        |
| dimension    |

| &lt;marker&gt; |
|----------------|
| Property       |
| position       |
| type           |
| size           |
| color          |
| interior       |
| dimension      |

| &lt;object&gt; |
|----------------|
| Property       |
| model          |
| position       |
| rotation       |
| interior       |
| dimension      |

| &lt;ped&gt; |
|-------------|
| Property    |
| position    |
| model       |
| rotZ        |
| interior    |
| dimension   |

| &lt;pickup&gt; |
|----------------|
| Property       |
| position       |
| type           |
| amount         |
| respawn        |
| interior       |
| dimension      |

| &lt;vehicle&gt; |
|-----------------|
| Property        |
| model           |
| position        |
| rotation        |
| color           |
| upgrades        |
| plate           |
| interior        |
| dimension       |

| &lt;radararea&gt; |
|-------------------|
| Property          |
| posX              |
| posY              |
| sizeX             |
| sizeY             |
| color             |
| dimension         |

### Built-in property names

Properties with these names have a special meaning to the editor and can be modified by other means than the Properties window.

| Name     | Type    |
|----------|---------|
| position | coord3d |
| rotation | coord3d |

### Property types

These are the types you can choose from for the properties (&lt;data&gt;) of your custom elements.

#### Primitives

| Name    | Description                              | Value                    |
|---------|------------------------------------------|--------------------------|
| boolean | Simple boolean value.                    | “true” or “false”        |
| natural | Natural number (whole and non-negative). |                          |
| integer | Whole number.                            |                          |
| number  | Rational number.                         |                          |
| string  | Simple string of text.                   |                          |
| color   | color, with or without alpha.            | 1.  RRGGBB or \#RRGGBBAA |

#### Coordinates

| Name    | Description                                                     | Value                                  |
|---------|-----------------------------------------------------------------|----------------------------------------|
| camera  | Position and lookat coordinates for the camera.                 | posX,posY,posZ,lookatX,lookatY,lookatZ |
| coord3d | 3-component vector, typically used for positions and rotations. | x,y,z                                  |

#### Vehicles

| Name            | Description                      | Value                               |
|-----------------|----------------------------------|-------------------------------------|
| plate           | Number plate text for a vehicle. |                                     |
| vehiclecolors   | colors of a vehicle              | colorID1,colorID2,colorID3,colorID4 |
| vehicleupgrades | Upgrades of a vehicle            | upgradeID1,upgradeID2,...           |

#### Model ID's

| Name       | Description             | Value                                  |
|------------|-------------------------|----------------------------------------|
| blipID     | Picture ID for blips    |                                        |
| objectID   | Model ID for objects    |                                        |
| pickupType | Armor, health or weapon | “armor”, “health” or numeric weapon ID |
| skinID     | Skin ID for peds        |                                        |
| vehicleID  | Model ID for vehicles   |                                        |
| weaponID   | Weapon, e.g. M4         | Numeric weapon ID, e.g. 31             |

#### Colshapes and markers

| Name         | Description                                         | Value                                                                  |
|--------------|-----------------------------------------------------|------------------------------------------------------------------------|
| colshapeType | collision circle, cube, rectangle, sphere or tube   | One of: “colcircle”, “colcube”, “colrectangle”, “colsphere”, “coltube” |
| markerType   | Arrow, checkpoint, corona, cylinder or ring marker. | One of: “arrow”, “checkpoint”, “corona”, “cylinder”, “ring”            |
||

#### Specials

| Name                    | Description                                          | Value              |
|-------------------------|------------------------------------------------------|--------------------|
| element:type            | Element of a certain type, for example: element:flag | The element's ID   |
| selection:val1,val2,... | Shows a dropdown box from which to pick one value.   | The selected value |

[ru:<Resource:Editor/EDF>](/docs/ru:resource:editor/edf.md "wikilink")
