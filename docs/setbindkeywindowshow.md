<pageclass class="#228B22" subcaption="Useful Function"></pageclass> <lowercasetitle/>

This function will hide window automatically and set BindKey to show it.

Syntax
------

``` lua
bool setBindKeyWindowShow ( element Window, string key )
```

### Required Arguments

-   **Window**: Window you want to edit it.
-   **key**: Key you want to enable it.

Code
----

<section name="Function source" class="client" show="true">
``` lua
setBindKeyWindowShow = function ( guiWindow, key )
    if guiWindow and key then
        if getElementType ( guiWindow ) == "gui-window" then
            guiSetVisible ( guiWindow, false );
            local setBindKey_ = function ( key )
                guiSetVisible ( guiWindow, not guiGetVisible ( guiWindow ) );
                showCursor ( guiGetVisible ( guiWindow ) );
            end
            return bindKey ( key, "down", setBindKey_ );
        else
            return false;
        end
    else
        return false;
    end
end
```

</section>

Example
-------

<section name="Client-side example" class="client" show="true">
This Example will hide window and showing it by BindKey.

``` lua
Window = guiCreateWindow ( 40, 40, 200, 200, "Test", false ) -- Create window.
setBindKeyWindowShow ( Window, "f2" ) -- Enable function on it.
```

</section>

-   This Function Has Created By **3NAD**.

See Also
--------

[Category:Useful Functions](/docs/category:useful_functions.md "wikilink")
