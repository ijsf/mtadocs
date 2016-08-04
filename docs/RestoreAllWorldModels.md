This function allows restoring of all world objects,which were removed with [RemoveWorldModel](/RemoveWorldModel.md "wikilink").

Syntax
------

``` lua
bool restoreAllWorldModels ( )
```

Returns
-------

Returns *true* if the world objects were restored, *false* otherwise.

Requirements
------------

Example
-------

This example adds command *“restoreallworldobjects”* that restores all world objects.

``` lua
addCommandHandler("restoreallworldobjects",
  function()
    restoreAllWorldModels()
  end
)
```

See Also
--------
