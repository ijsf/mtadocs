This function is used to determine if an object is in a group.

Syntax
------

``` lua
bool isObjectInACLGroup ( string theObject, aclgroup theGroup )
```

### Required Arguments

-   **theObject:** the name of the object to check. Examples: “resource.ctf”, “user.Jim”.
-   **theGroup:** the [ACL group](/docs/ACL_group.md "wikilink") pointer of the group from which the object should be found.

### Returns

Returns *true* if the object is in the specified group, *false* otherwise.

Example
-------

*' Example 1:*' This example adds a *jetpack* command that is only available to admins. When entering the command, it will toggle the player's jetpack.

``` lua
addCommandHandler ( "jetpack",
    function ( thePlayer )
        if doesPedHaveJetPack ( thePlayer ) then -- If the player have a jetpack already, remove it
            removePedJetPack ( thePlayer ) -- Remove the jetpack
            return -- And stop the function here
        end
        
     -- Otherwise, give him one if he has access

     local accName = getAccountName ( getPlayerAccount ( thePlayer ) ) -- get his account name
     if isObjectInACLGroup ("user."..accName, aclGetGroup ( "Admin" ) ) then -- Does he have access to Admin functions?
          if not doesPedHaveJetPack ( thePlayer ) then -- If the player doesn't have a jetpack give it.
               givePedJetPack ( thePlayer )  -- Give the jetpack
          end
     end
end
)
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
