This function is used to call a function from another resource (which must be running).

The function which you wish to call **must** first be exported within the resource's meta. For example:

``` xml
<meta>
    <info author="jbeta" type="script" description="Scoreboard resource" />
    <script src="scoreboard_client.lua" type="client"/>
    <script src="scoreboard_exports.lua" type="server"/>
    
    <script src="scoreboard_http.lua" type="server"/>
    
    <export function="getScoreboardColumns" http="true" />
    <export function="getScoreboardRows" http="true" />
    
    <export function="addScoreboardColumn" type="server"/>
    <export function="removeScoreboardColumn" type="server"/>
    
    <export function="setPlayerScoreboardForced" type="server"/>
    <export function="setScoreboardForced" type="client"/>
</meta>
```

This enables other resources to call a function from this resource.

You cannot call a server function from the client or vice versa. See [triggerServerEvent](/docs/triggerServerEvent.md "wikilink") and [triggerClientEvent](/triggerClientEvent.md "wikilink") for possibilities to do that.

There is an easier syntax replacing this function. For example, you can instead of:

``` lua
call ( getResourceFromName ( "resource" ), "exportedFunction", 1, "2", "three" )
```

do much like a normal call:

``` lua
exports.resource:exportedFunction ( 1, "2", "three" )
```

If the resource name contains illegal characters (such as hyphens), you can also do:

``` lua
:exportedFunction ( 1, "2", "three" )
```

When using the [call](/docs/call.md "wikilink") function, two extra “hidden” variables are passed to the exported function:

-   **sourceResource** - The resource that called the exported function
-   **sourceResourceRoot** - The resource root element of the resource which called the exported function.

Syntax
------

``` lua
var... call ( resource theResource, string theFunction, [ arguments... ] )
```

### Required Arguments

-   **theResource:** This is a resource pointer which refers to the resource you are calling a function from.
-   **theFunction:** This is a string with the name of the function which you want to call.

### Optional Arguments

-   **arguments:** Any arguments you may want to pass to the function when it is called. Any number of arguments of can be specified, each being passed to the designated function.

### Returns

Returns anything that the designated function has returned appropriately. If the function does not exist, is not exported, or the call was not successful it will return *nil*.

Example
-------

<section name="Server" class="server" show="true">
This extract shows adding of a “kills” column to the scoreboard resource. This then sets the *gameShowKills* variable to true, telling the rest of the script to start outputting kills.

``` lua
function showKills ( option )
    if option == false then
        -- Remove the "kills" column
        gameShowKills = false
        call(getResourceFromName("scoreboard"), "removeScoreboardColumn", "kills")
    else
        -- Add the "kills" column
        gameShowKills = true
        call(getResourceFromName("scoreboard"), "addScoreboardColumn", "kills")
        outputDebugString ( "Showing kills now..." )
    end
end
```

</section>
See Also
--------
