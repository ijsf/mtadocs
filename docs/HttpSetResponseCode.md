This function sets the HTTP status code that will be sent for the current HTML page.

Syntax
------

``` lua
bool httpSetResponseCode ( int code )
```

Required Arguments
------------------

-   **code:** the HTTP status code to be set.

### Returns

Returns *true* if the code was set successfully, *false* otherwise.

Example
-------

<section name="Server/HTTP" class="http" show="true">
This example displays a 'Page not found' error message and the response code 404. The location of the [httpSetResponseCode](/httpSetResponseCode.md "wikilink") call is unimportant - it can be placed anywhere in the document.

``` html
<html>
<h1>Page not found!</h1>
<* httpSetResponseCode ( 404 ) *>
</html>
```

</section>
See Also
--------
