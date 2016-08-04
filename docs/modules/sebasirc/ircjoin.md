This function joins the bot a channel (, with a password).

Syntax
------

``` lua
bool ircJoin(string channel [, string password])
```

### Required arguments

-   **channel:** The channel name.

### Optional Arguments

-   **password:** The channel password.

### Returns

*True* if joined, otherwise *false*.

Example
-------

``` lua
addEventHandler("onResourceStart", getResourceRootElement(),
  function()
    local connect = ircConnect("irc.mtasa.com", 6667, "MTABot")
    if connect then
      ircJoin("#mta.test")
    end
  end
)
```

[pl:Modules/SebasIRC/ircJoin](/docs/pl-modules/sebasirc/ircjoin.md "wikilink")

See also
--------
