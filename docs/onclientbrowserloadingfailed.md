Parameters
----------

``` lua
string url, int errorCode, string errorDescription
```

-   **url:** The requested URL
-   **errorCode:** See below
-   **errorDescription:** A short description

Source
------

The [browser](/docs/Element/Browser.md "wikilink") element

Error codes
-----------

| Name                                     | Error code |
|------------------------------------------|------------|
| ERR\_NONE                                | 0          |
| ERR\_FAILED                              | -2         |
| ERR\_ABORTED                             | -3         |
| ERR\_INVALID\_ARGUMENT                   | -4         |
| ERR\_INVALID\_HANDLE                     | -5         |
| ERR\_FILE\_NOT\_FOUND                    | -6         |
| ERR\_TIMED\_OUT                          | -7         |
| ERR\_FILE\_TOO\_BIG                      | -8         |
| ERR\_UNEXPECTED                          | -9         |
| ERR\_ACCESS\_DENIED                      | -10        |
| ERR\_NOT\_IMPLEMENTED                    | -11        |
| ERR\_CONNECTION\_CLOSED                  | -100       |
| ERR\_CONNECTION\_RESET                   | -101       |
| ERR\_CONNECTION\_REFUSED                 | -102       |
| ERR\_CONNECTION\_ABORTED                 | -103       |
| ERR\_CONNECTION\_FAILED                  | -104       |
| ERR\_NAME\_NOT\_RESOLVED                 | -105       |
| ERR\_INTERNET\_DISCONNECTED              | -106       |
| ERR\_SSL\_PROTOCOL\_ERROR                | -107       |
| ERR\_ADDRESS\_INVALID                    | -108       |
| ERR\_ADDRESS\_UNREACHABLE                | -109       |
| ERR\_SSL\_CLIENT\_AUTH\_CERT\_NEEDED     | -110       |
| ERR\_TUNNEL\_CONNECTION\_FAILED          | -111       |
| ERR\_NO\_SSL\_VERSIONS\_ENABLED          | -112       |
| ERR\_SSL\_VERSION\_OR\_CIPHER\_MISMATCH  | -113       |
| ERR\_SSL\_RENEGOTIATION\_REQUESTED       | -114       |
| ERR\_CERT\_COMMON\_NAME\_INVALID         | -200       |
| ERR\_CERT\_DATE\_INVALID                 | -201       |
| ERR\_CERT\_AUTHORITY\_INVALID            | -202       |
| ERR\_CERT\_CONTAINS\_ERRORS              | -203       |
| ERR\_CERT\_NO\_REVOCATION\_MECHANISM     | -204       |
| ERR\_CERT\_UNABLE\_TO\_CHECK\_REVOCATION | -205       |
| ERR\_CERT\_REVOKED                       | -206       |
| ERR\_CERT\_INVALID                       | -207       |
| ERR\_CERT\_END                           | -208       |
| ERR\_INVALID\_URL                        | -300       |
| ERR\_DISALLOWED\_URL\_SCHEME             | -301       |
| ERR\_UNKNOWN\_URL\_SCHEME                | -302       |
| ERR\_TOO\_MANY\_REDIRECTS                | -310       |
| ERR\_UNSAFE\_REDIRECT                    | -311       |
| ERR\_UNSAFE\_PORT                        | -312       |
| ERR\_INVALID\_RESPONSE                   | -320       |
| ERR\_INVALID\_CHUNKED\_ENCODING          | -321       |
| ERR\_METHOD\_NOT\_SUPPORTED              | -322       |
| ERR\_UNEXPECTED\_PROXY\_AUTH             | -323       |
| ERR\_EMPTY\_RESPONSE                     | -324       |
| ERR\_RESPONSE\_HEADERS\_TOO\_BIG         | -325       |
| ERR\_CACHE\_MISS                         | -400       |
| ERR\_INSECURE\_RESPONSE                  | -501       |

Example
-------

``` lua
addEventHandler("onClientBrowserLoadingFailed", root,
    function(url, errorCode, errorDescription)
        outputChatBox("This webpage is not available" .. url .. "Unknown" .. errorCode .. "Unknown" .. errorDescription)
    end
)
```

[pl:onClientBrowserLoadingFailed](/docs/pl:onClientBrowserLoadingFailed.md "wikilink")

See Also
--------
