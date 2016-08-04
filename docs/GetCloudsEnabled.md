This function will tell you if clouds are enabled or disabled.

Syntax
------

``` lua
bool getCloudsEnabled ()
```

### Returns

Returns *true* if the clouds are enabled or *false* if clouds are disabled.

Example
-------

``` lua
function areCloudsVisible()
  if getCloudsEnabled() then
    outputChatBox("Clouds are visible.")
  else
    outputChatBox("Clouds are not visible.")
  end
end
addCommandHandler("clouds", areCloudsVisible)
```

See Also
--------

[ru:getCloudsEnabled](/docs/ru:getCloudsEnabled.md "wikilink")
