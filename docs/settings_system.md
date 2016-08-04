The settings system allows you to store and retrieve settings for future use, or provide server administrators with an easy way to configure your resource without modifying any files.

Settings can be modified in two ways - either by scripts or by the server administrator using the console.

Setting names
-------------

Settings have a fairly simple naming system that allows you to specify the *scope* and *access* they provide.

Names are in the format:

\[*access*\]\[*resourceName*\].*settingName*

Access modifiers:

-   **\***: *public* and can be read and written by any resource.
-   **\#**: *protected* and can be read by any resource but only written by the resource they belong to.
-   **@**: *private* and can only be read and written to by the resource they belong to.
-   None specified: *private* if it is a local setting, *public* if it's a global setting.

The *resourceName* is optional. If it isn't specified, then the setting is *global*.

The *settingName* can be anything you want.

Manager
-------

You can manage your settings with the default [admin](/docs/resource:admin.md "wikilink") manager resource. In addition you can add some attributes in a setting, which will be useful in the settings manager:

``` xml
<settings>
    <setting name="*settingname" value="defValue" friendlyname="" group="" accept="" examples="" desc="" />
</settings>
```

-   **Explanation:** <small>TODO</small>

:\***friendlyname:** A friendly name to the setting.

:\***accept:** The values the setting could accept.

:\***examples:** An Example of a value.

:\***desc:** A description of the setting.

Scripting functions
-------------------

There are two scripting functions in the setting system: [set](/docs/set.md "wikilink") and [get](/get.md "wikilink").

Console functions
-----------------

There are two console functions in the settings system:
