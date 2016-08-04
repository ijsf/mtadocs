The *meta.xml* file presents MTA with a set of metadata, such as the resource's name, the scripts to include, and which files to precache for sending to clients among other things. It is also the scope of “elements”. It is written in XML, which is based on HTML and is the parent of XHTML.

Tags
====

XML is a textual data format which is widely used for the representation of data. MTA uses an XML-based language to describe the metadata for resources by using the tags below:

-   **<info />** Information about this resource, possible parameters include (any arbitrary parameters can be used and read using [getResourceInfo](/docs/getresourceinfo.md "wikilink")):
    -   **author:** The author of this resource
    -   **version:** The version of this resource
    -   **name:** The name of this resource
    -   **description:** A brief description of this resource
    -   **type:** The type of this resource, that can be “gamemode”, “script”, “map” or “misc”.
-   '''
    <script />
    ''' Source code for this resource, possible parameters are:

    -   **src:** The file name of the source code
    -   **type:** The type of source code: “client”, “server” or “shared”.
    -   **cache:** When the script file type is “client”, this setting controls whether the file is saved on the clients' hard drive. Default is “true”. Using “false” will mean the file is not saved. *(Note: cache=false files are started at the client first, so lua file load order might differ when mixing cache settings)*
    -   **validate:** If set to “false”, compatibility checks are skipped.
-   **<map />** The map for a gamemode, possible parameters are:
    -   **src:** .map file name (can be path too eg. “maps/filename.map”)
    -   **dimension:** Dimension in which the map will be loaded (optional)
-   **<file />** A client-side file. Generally these are images, .txd, .col, .dff or .xml files. They'll be downloaded by clients when the resources is started (or on join)
    -   **src:** client-side file name (can be path too eg. “images/image.png”)

<!-- -->

-   **<include />** Include resources that this resource will use
    -   **resource:** Resource name that you want to start with this resource
    -   **minversion:** Minimum version that **resource** needs to be (optional)
    -   **maxversion:** Maximum version that **resource** needs to be (optional)
-   **<config />** Config file (.xml) can be accessed by resource, possible parameters are:
    -   **src:** The file name of the config file
    -   **type:** The type of the config file: “client” or “server”
-   **<export />** This exports functions from this resource, so other resources can use them with [call](/docs/call.md "wikilink")
    -   **function:** The function name
    -   **type** Whether function is exported server-side or client-side (valid values are: “client”, “server” and “shared”)
    -   **http:** Can the function be called via HTTP (true/false)
-   '''
    <html />
    '''

    -   **src:** The filename for the HTTP file (can be a path)
    -   **default:** The html file is one that is shown by default when visiting /resourceName/ on the server. Only one html can be default, the rest are ignored. (true/false)
    -   **raw:** The html file is not parsed by the Lua interpreter and is treated as binary data. Must be used for binary files (images mainly) (true/false)
-   **<settings> <setting name="" value=""/> </settings>:** Most gamemodes use [settings system](/docs/settings_system.md "wikilink") to let server admins to configure it how they like. For instance you could set round time and then use [get](/docs/get.md "wikilink") and [set](/docs/set.md "wikilink") to get the value or change it, respectively.
-   **<min_mta_version />** Minimum version requirements for this resource to run correctly. When authoring resources, the minimum version should usually be set to the current released version of MTA:SA (which at the moment is ""). See example for example.
    -   **client:** The minimum client version
    -   **server:** The minimum server version
-   **<aclrequest />** A list of [ACL](/docs/access_control_list.md "wikilink") rights this resource will need.

Example
-------

Heres an example of a meta file using some of the tags mentioned: {{\#tag:code | <meta>

`   `<info author="Slothman" type="gamemode" name="Stealth" />
`   `<config src="help.xml" type="client"/>

`   `<download_priority_group>`0`</download_priority_group>
`   `<min_mta_version client="{{Current Version|full}}" server="{{Current Version|full}}" />

`   `<sync_map_element_data>`false`</sync_map_element_data>

<script src="stealthmain_server.lua" />
<script src="noiseblip.lua" />
<script src="mission_timer.lua" />
<script src="gadgets_server.lua" />
<script src="gadgets_client.lua" type="client"/>
<script src="stealthmain_client.lua" type="client" validate="true"/>
<script src="noisebar.lua" type="client"/>
<script src="spycam.lua" type="client"/>
<script src="riemann_z_demonstration.lua" type="client" cache="false"/>
`   `<map src="base.map" dimension="1"/>

`   `<file src="riot_shield.txd" />
`   `<file src="riot_shield.dff" />
`   `<file src="riot_shield.col" />
`   `<file src="armor.png"/>
`   `<file src="camera.png"/>
`   `<file src="cloak.png" />
`   `<file src="goggles.png" />
`   `<file src="mine.png" />
`   `<file src="radar.png" />
`   `<file src="shield.png" />

`   `<include resource="scoreboard" />
`   `<include resource="killmessages" />
`   `<include resource="maplimits" />
`   `
`   `<export function="exampleExport1" type="server" />
`   `<export function="exampleExport2" type="client" />
`   `<export function="exampleExport3" type="shared" />

`   `<settings>
`        `<setting name="roundlimit" value="[6]" />` `
`    `<setting name="teamdamage" value="[1]" />` `
`    `<setting name="teambalance" value="[1]" />` `
`    `<setting name="spazammo" value="[25]" />` `
`    `<setting name="m4ammo" value="[100]" />
`    `<setting name="shotgunammo" value="[25]" />
`    `<setting name="sniperammo" value="[20]" />
`    `<setting name="ak47ammo" value="[120]" />
`    `<setting name="rifleammo" value="[40]" />
`    `<setting name="deserteagleammo" value="[45]" />
`    `<setting name="pistolammo" value="[132]" />
`    `<setting name="uziammo" value="[150]" />
`    `<setting name="tec9ammo" value="[150]" />
`    `<setting name="silencedammo" value="[65]" />
`    `<setting name="grenadeammo" value="[4]" />
`    `<setting name="satchelammo" value="[4]" />
`    `<setting name="teargasammo" value="[4]" />
`    `<setting name="molatovammo" value="[4]" />
`    `<setting name="isAllowedToShoot" value="true" />
`    `</settings>

`    `<aclrequest>
`    `<right name="function.startResource" access="true" />
`    `<right name="function.stopResource" access="true" />
`    `<right name="function.setPlayerMuted" access="true" />
`    `</aclrequest>

</meta> |lang=“xml”}} [Category:Scripting Concepts](/docs/category-scripting_concepts.md "wikilink") [cs:Meta.xml](/docs/cs-meta.xml.md "wikilink") [de:Meta.xml](/docs/de-meta.xml.md "wikilink") [es:Sobre el archivo “meta.xml”](/docs/es-sobre_el_archivo_"meta.xml".md "wikilink") [it:Meta.xml](/docs/it-meta.xml.md "wikilink") [pl:Meta.xml](/docs/pl-meta.xml.md "wikilink") [ru:Meta.xml](/docs/ru-meta.xml.md "wikilink")
