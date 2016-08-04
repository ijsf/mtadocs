<lowercasetitle/>

This function gets the server ip.

Syntax
------

``` string
string getServerIp ( )
```

Code
----

<section name="Server" class="server" show="true">
``` lua
SERVER_IP = "127.0.0.1"

function getServerIp()
    return SERVER_IP
end

fetchRemote("http://checkip.dyndns.com/",
    function (response)
        if response ~= "ERROR" then
            SERVER_IP = response:match("<body>Current IP Address: (.-)</body>") or "127.0.0.1"
        end
    end
)
```

</section>
Example
-------

<section name="Server" class="server" show="true">
``` lua
outputServerLog("Public server IP: " .. getServerIp())
```

</section>
Credits
-------

-   **Author:** MJNONFIK
-   **Edited by:** Necktrox

See Also
--------
