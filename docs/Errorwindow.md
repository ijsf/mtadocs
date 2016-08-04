This resource provides a function that shows an dx-errorwindow. The window's size will fit the text that you put into it.

Example (top -&gt; errorwindow, bottom -&gt; infowindow):

[Image:errorwindow.png](/Image:errorwindow.png.md "wikilink")

In its settings, you can set the color of:

-   Top-background (red, green, blue, alpha) (0-255)
-   Top-text (red, green, blue) (0-255)
-   Text-background (red, green, blue, alpha) (0-255)
-   Text (red, green, blue) (0-255)

Download
--------

<http://community.multitheftauto.com/index.php?p=resources&s=details&id=4921>

Syntax
------

<section name="Server" class="server" show="true">
``` lua
exports.errorwindow: show ( player thePlayer, string text, [ int time = 0, string toptext = "ERROR", bool disableByClick = true ] )
```

### Required Arguments

-   **thePlayer:** Player to show the errorwindow to.
-   **text:** Text to show in the errorwindow.

### Optional Arguments

-   **time:** Time in milliseconds to show the window, before it disappears (if disableByClick is true and client clicks, timer is overridden).
-   **toptext:** Text in the top of the window (“Scumbag customer” in example-image above).
-   **disableByClick:** Close window when client clicks somewhere (**cursor must be enabled!**).

</section>
<section name="Client" class="client" show="true">
``` lua
exports.errorwindow: show ( string text, [ int time = 0, string toptext = "ERROR", bool disableByClick = true ] )
```

### Required Arguments

-   **text:** Text to show in the errorwindow.

### Optional Arguments

-   **time:** Time in milliseconds to show the window, before it disappears (if disableByClick is true and client clicks, timer is overridden).
-   **toptext:** Text in the top of the window (“Scumbag customer” in example-image above).
-   **disableByClick:** Close window when client clicks somewhere (**cursor must be enabled!**).
