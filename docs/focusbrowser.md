Syntax
------

``` lua
bool focusBrowser ( browser webBrowser )
```

### Required Arguments

-   **webBrowser:** The web browser to be focused - if this is **nil**, it will unfocus all browsers.

### Returns

Returns *true* if the browser was focused or if nil was passed, *false* if it failed to focus or the browser does not exist.

Example
-------

<section name="Client" class="client" show="true">
This example creates browser and focus it

``` lua
local browser = createBrowser(860, 680, false)
addEventHandler("onClientBrowserCreated", browser,
   function ()
       focusBrowser(source)
   end
)
```

</section>
See Also
--------
