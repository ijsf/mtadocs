Syntax
------

``` lua
bool setBanNick ( ban theBan, string theNick )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") you want to change the nick of.
-   **theNick:** A string representing the nick you want to set the ban to.

### Returns

Returns *true* if changed, *false* otherwise.

Example
-------

``` lua
-- this example looks if there is a ban with nick 'Steve', and if there is, it changes ban nick to 'Mike'
function changeBanNick()
   for i,ban in pairs(getBans()) do
      if getBanNick(ban) == "Steve" then
         setBanNick(ban,"Mike")
      end
   end
end
addCommandHandler("setbannick",changeBanNick)
```

See Also
--------
