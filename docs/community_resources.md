This page lists PHP calls that MTA Community allows you to use in your scripts, via [callRemote](/docs/callremote.md "wikilink").

community.mtasa.com/mta/resources.php
-------------------------------------

Retrieves the latest version number for a resource available on MTA Community.

**Arguments**:

``` lua
string "version", string resourceName
```

**Returns:**

-   a string with the resource name
-   a string of the resource version in format of “x.x.x”, or integer 0 if an error has occurred
-   a number which is the community id for the resource, or nil if an error has occurred

### Example

    addEventHandler( "onResourceStart", getResourceRootElement(), 
       function()
          callRemote( "http://community.mtasa.com/mta/resources.php", handleVersionCheck, "version", getResourceName(getThisResource()) )
       end
    )

    function handleVersionCheck( resName, commVer, commId )
        local thisVer = getResourceInfo(getThisResource(), "version")
        if commId and thisVer ~= commVer then
            outputChatBox( getResourceName(getThisResource()) .. " is outdated. Your version: " .. thisVer .. " | Current: " .. commVer )
            outputChatBox( "Please download the update @ http://community.multitheftauto.com/index.php?p=resources&s=details&id=" .. commId )
        end
    end

community.mtasa.com/mta/groups.php
----------------------------------

Retrieves group information from MTA Community.

**Arguments**:

``` lua
string "info", int groupID
```

**Returns 5 values:**

-   Group name
-   Owner username
-   Number of members
-   Public. Integer: 1 if the group is public, 0 otherwise
-   Registration time

Members list:

``` lua
string "members", int groupID
```

**Returns:** a table of usernames in the group

### Examples

<section name="Group Example" class="server" show="false">
This outputs the servers group name, if the group is public or private, and the registration time.

``` lua
addEventHandler("onPlayerJoin",getRootElement(),function()
   callRemote("http://community.mtasa.com/mta/groups.php",info,"info",1) --When the player joins, call the site for the info
end)

function info(groupName,ownerUser,members,public,registrationTime) --Define all the values
   if(groupName)and(public)and(registrationTime)then --check if the info came through
      outputChatBox("Our group is in the MTA Community Site, it's called: "..groupName..", our groups is "..public.." and was registered in"..registrationTime..".",source,0,100,100) --output about the servers new/existing group
   end
end
```

</section>
<section name="Members Example" class="server" show="false">
This outputs the members in the servers group, which is found on the MTA Community Site.

``` lua
addCommandHandler("members",function(player)
   callRemote("http://community.mtasa.com/mta/groups.php",members,"members",1)--Call after the command goes through
end)

function members(player,members)
   if(members)then
      outputChatBox("Members in this servers group: "..members..".",player,255,255,255) --Outputs the members to the player who typed in the command
   end
end
```

</section>
[Category:Scripting Concepts](/docs/category-scripting_concepts.md "wikilink")
