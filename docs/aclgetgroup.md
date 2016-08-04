This function is used to get the ACL group with the given name. If you need most of the groups you should consider using [aclGroupList](/docs/aclGroupList.md "wikilink") instead to get a table containing them all.

Syntax
------

``` lua
aclgroup aclGetGroup ( string groupName )
```

### Required Arguments

-   **groupName:** The name to get the ACL group from

### Returns

Returns the ACL group if it could be found. Returns *false*/*nil* if it did not exist or failed for some reason.

Example
-------

**Example 1:** This example makes every player able to use a command named “giveAccountAdminRights” that will add a specific accountname as an ACL object to the “Admin” group.

``` lua
function giveAdminRights (playerSource, commandName, accountName) --add the function giveAdminRights and specify its arguments
    if accountName then --if there was an accountName entered then
        aclGroupAddObject (aclGetGroup("Admin"), "user."..accountName)) --add an ACL object using the form "user.[accountName]" to the ACL group "Admin"
        outputChatBox ("Account '"..accountName.."' succesfully added to the admin group", playerSource) --output a notification to the player who entered the command that the acocunt was successfully added
    else --else output an error message and the correct syntax of the command to the player who entered it
        outputChatBox ("No account name specified.", playerSource)
        outputChatBox ("Correct syntax: /giveAccountAdminRights [accountName]", playerSource)
    end
end

addCommandHandler ("giveAccountAdminRights", giveAdminRights) --add a command "giveAccountAdminRights" and attch the function "giveAdminRights" to it 
```

**Example 2:** This example displays a list of all the online admins in the chat box (assuming your administrator's group in your ACL is called 'admin'):

``` lua
players = getElementsByType ( "player" )
admins = ""
for k,v in ipairs(players) do
   local accountname = ""
   if (isGuestAccount(getPlayerAccount(v)) == false) then
      accountname = getAccountName (getPlayerAccount(v))
      if isObjectInACLGroup ( "user." .. accountname, aclGetGroup ( "admin" ) ) then
         if (admins == "") then
            admins = getPlayerName(v)
         else
            admins = admins .. ", " .. getPlayerName(v)
         end
      end
   end
end
outputChatBox( "Online Admins:", getRootElement(), 255, 255, 0)
outputChatBox( " " .. tostring ( admins ), getRootElement(), 255, 255, 0)
```

See Also
--------
