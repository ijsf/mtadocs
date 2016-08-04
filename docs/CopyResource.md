This function copies a specified [resource](/resource.md "wikilink") with a new name.

Syntax
------

``` lua
resource copyResource ( resource theResource, string newResourceName [, string organizationalDir ] )
```

### Required Arguments

-   **theResource:** the resource which is going to be copied
-   **newResourceName:** the name that the copied resource will receive

### Optional Arguments

-   **organizationalDir**: A string containing the path where the resource should be copied to (e.g. "\[gamemodes\]/\[amx\]").

### Returns

Returns the [resource](/resource.md "wikilink") element of the copy. Returns *false* if the arguments are incorrect.

Example
-------

``` lua
-- This script can backup your resource with a easy command! /backupresource [resourcename]
function backupResource (player,command,resourcetobackup) -- start the function
  if (resourcetobackup) and (getResourceFromName(resourcetobackup)) then -- check if the resource is exist
    copyResource (getResourceFromName(resourcetobackup),resourcetobackup .. "_backup") -- copy the resource and give it the name [resource]_backup
    outputChatBox ("Resource " .. resourcetobackup .. " succesfully backed up!",player,255,0,0,false) -- say it's OK!
  else -- if it isn't exist
    outputChatBox ("Resource can't be backed up! (don't forget the parameters!)",player,255,0,0,false) -- say it isn't exist!
  end
end
addCommandHandler ("backupresource",backupResouce) -- add command
```

Requirements
------------

See Also
--------
