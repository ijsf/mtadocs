The [account](/docs/account.md "wikilink") class represents a [player](/player.md "wikilink")'s server account. You can get the [account](/account.md "wikilink") object associated to any client using [getPlayerAccount](/getPlayerAccount.md "wikilink").

Accounts are unique to each client and can be used to store information that is persistent across map changes and user sessions. Clients that join without an account are given a temporary 'guest' account. This can store information like any other account, but isn't saved across sessions.

When a user logs in or out, the account object assigned to them will change. As such, you must not assume that the account attached to a client remains constant during their session.

PHP code to check password hashes from the MTA server database is [here.](/docs/account_php.md "wikilink")

Related scripting functions
---------------------------

### Server

[Category:Scripting Concepts](/docs/category:scripting_concepts.md "wikilink")

[it:Account](/docs/it:account.md "wikilink") [de:Account](/de:Account.md "wikilink") [ru:Account](/ru:Account.md "wikilink")
