Syntax
------

``` lua
bool isBan ( ban theBan )
```

### Required Arguments

-   **theBan:** The value to check

### Returns

Returns *true* if the value is a ban, *false* otherwise.

Example
-------

<section name="Example1" class="server" show="true">
This example chechks if the passed argument is a ban or not.

``` lua
function banRecieve ( ban )
if ban and isBan(ban) == true then
outputChatBox("this is a ban!")--Valid ban is recieved!
else
outputChatBox("this is not a ban, this is a "..getElementType(ban))--if the argument is not a ban, then checks its type and output it into the chat box.
end
end


function onBan ( ban ) -- This function will be triggered every time a player is banned.
banRecieve(ban)
end
addEventHandler ( "onPlayerBan", getRootElement(), onBan )


function sendWrongBanArguement()
vehicle = createVehicle(411,0,5,3)
object = createObject(2600,0,0,0)
ped = createPed(61,0,0,3)
banRecieve(vehicle)--sends a vehicle as an argument.
banRecieve(object)--sends an object as an argument.
banRecieve(ped)--sends a ped as an argument.
end
addCommandHandler("sendWrongArgument",sendWrongBanArguement)
```

</section>
See Also
--------

[ru:isBan](/docs/ru-isban.md "wikilink")
