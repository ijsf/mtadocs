This function starts a resource either persistently or as a dependency of the current resource. If you start the resource persistently, the resource will run until stopped either using [stopResource](/docs/stopresource.md "wikilink") or by the server admin. A resource started as a dependency will stop when your resource stops, if no other resources have it as a depdendency. This is the same effect as using an *include* in your [meta.xml](/meta.xml.md "wikilink") file.

The function also allows you to specify a number of boolean options. These allow you to disable the loading of various aspects of the resource. This is generally useful for editors rather than for actual gamemodes. It could also be used as a way to preview a resource before enabling the scripting aspects, though this could produce unreliable results. There is no way for a resource to tell if it is being run with any of these booleans set.

Syntax
------

``` lua
bool startResource ( resource resourceToStart, [bool persistent = false, bool startIncludedResources = true, bool loadServerConfigs = true, bool loadMaps = true, bool loadServerScripts = true, bool loadHTML = true, bool loadClientConfigs = true, bool loadClientScripts = true, bool loadFiles = true] )
```

### Required Arguments

-   **resourceToStart:** The resource that should be started.

### Optional Arguments

-   **persistent:** A boolean specifying if the resource should continue to run even after this resource has been stopped or not. If this is *true* then the resource will run until another resource or user terminates it or the server shuts down.
-   **startIncludedResources:** A boolean specifying if the resource's included/dependant resources will be started.
-   **loadServerConfigs:** A boolean specifying if server side config (XML) files should be loaded with the resource.
-   **loadMaps:** A boolean specifying if any .map files will be started with the resource.
-   **loadServerScripts:** A boolean specifying if server side script files should be started alongside the resource.
-   **loadHTML:** A boolean specifying if HTML files should be started alongside the resource.
-   **loadClientConfigs:** A boolean specifying if client configs should be loaded alongside the resource.
-   **loadClientScripts:** A boolean specifying if client scripts should be loaded and started alongside the resource.
-   **loadFiles:** A boolean specifying if client-side files should be loaded alongside the resource.

### Returns

Returns *true* if the resource has been started successfully, *false* otherwise.

Example
-------

This example starts a specified resource with the command; "/resource-start".

``` lua
function startTheResource ( thePlayer, command, resourceName )
    if ( resourceName ) then -- Check if they specified a resource name
        local resource = getResourceFromName ( resourceName ) -- Get the resource
        
        local start = startResource ( resource ) -- Start the resource
        if ( start ) then -- If it was successfully started...
            outputChatBox ( resourceName .. " was started successfully.", thePlayer, 255, 0, 0 )
        else -- If it wasn't successfully started...
            outputChatBox ( "This resource doesn't exist.", thePlayer, 255, 0, 0 )
        end
    else -- If they didn't put a resource name...
        outputChatBox ( "Please specify a resource to start.", thePlayer, 255, 0, 0 )
    end
end
addCommandHandler ( "resource-start", startTheResource ) -- Make it trigger when somebody types "/resource-start"
```

See Also
--------
