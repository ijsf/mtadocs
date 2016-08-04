Resources are a key part of MTA. A resource is essentially a folder or zip file that contains a collection of files - including script files, plus a *meta* file that describes how the resource should be loaded. A resource can be seen as being partly equivalent to a program running in an operating system - it can be started and stopped, and multiple resources can run at once. Its worth remember though, that unlike programs on an operating system, there is no multi-tasking between resources.

Terminology
-----------

-   **Resource** - A zip file or folder containing a meta.xml file and a number of resource items. These are placed in the *mods/deathmatch/resources* folder in the server directory.
-   **Resource item** - A file contained within a resource, currently this can be a map, script, images etc.

The Meta File
-------------

*See main article [Meta.xml](/docs/meta.xml.md "wikilink") for details*

The Meta file is the core of each the resource. It describes exactly what files in the resource should be used, and how. The following is an example that covers every option there is, your meta files can have as many or as few of these tags as you require:

``` xml
<meta>
    <info author="eAi" description="This is a basic CTF script" version="4"/>

    <include resource="radarblips"/>
    <include resource="markermanagement" />

    <script src="ctf.lua" />
    <script src="flag.lua" />
    <script src="ctf_client.lua" type="client" />

    <file src="model.dff" />
    <file src="quitbutton.png" />
    <file src="killed.png"  />

    <html src="test.htm" default="true"/>
    <html src="logo.png" raw="true" />

    <export function="multiply" http="true" />
    <export function="getPlayerList" />
    <export function="getElementOwner" type="client"/>

    <config src="vehicle-list.xml" type="client" />
    <config src="markerconfig.xml" type="server"  />

    <map src="somestuff.map" dimension="99" />
</meta>
```

While a CTF map may have a meta.xml that looks like:

``` xml
<meta>
    <include resource="ctf" />
    <map src="myuberl33tctfmap.map" />

    <info author="Tom" instructions="this is uber l33t !!!!!1111111" type="map" />
</meta>
```

Script/type, Config/type and File/type attributes specify if the script/resource should be sent to clients or not, and defaults to “server”.

The include tag specifies other resources that should be started before this resoucre is started. In other words, if your resource is dependent on another, you can include it so that the other resource is started first,

Each resource has its own virtual machine (VM). This contains every script in the resource. This means that variables are not shared with other resources. The best way to communictate with other resources is by using the *export* tag and exporting a function. This will enable other resources to fire this function using the [call](/docs/call.md "wikilink") scripting function.

Scripts sent to clients are started as soon as all the scripts have been downloaded.

Scripts are able to read and write to their own resource folder with functions such as [xmlCreateFile](/docs/xmlcreatefile.md "wikilink") and [fileCreate](/docs/filecreate.md "wikilink"). They can also read and write to other resources, but must have [ACL](/docs/access_control_list.md "wikilink") access.

Each resource can only be loaded once, the server will ensure this. If a resource is included more than once, the same instance will be used by each resource that includes it.

File storage
------------

Resource files can either be stored in a zip or a directory. This is located in:

server/mods/deathmatch/resources/ (if you've installed your server with the client)

or

mods/deathmatch/resources/ (for dedicated server installations)

Each resource can have a zip file, a directory or both. In the case of both existing, the directory has precedence over the zip file, as such files can be placed in the directory to over-ride the files in the zip file. This allows directories to be used for testing and developing of maps/scripts while zip files used by end-users.

Other things to note
--------------------

-   Resource names can't have dots in.
-   If the resource does any file saving, the file names used should not be listed in the meta.xml
-   Files listed in the meta.xml should be considered read only by your scripts. Do not modify them with xmlSaveFile, FileSave etc.
-   When making a zip file of your resource, do not include save files. If your resource uses save files, they must be created by your resource when needed.
-   When making a zip file of your resource, only include files that are listed in the meta.xml. Do not include 'example' save files, otherwise bad things will happen.
-   We recommend avoiding spaces and exotic characters from resources names.

Script functions
----------------

The resource system can be manipulated by script. As such, the following Serverside scripting functions are provided:

The following events are also provided:

[it:Introduzione alle Risorse](/docs/it:introduzione_alle_risorse.md "wikilink") [pt-br:Recursos](/docs/pt-br:recursos.md "wikilink") [ru:Resources](/docs/ru:resources.md "wikilink")
