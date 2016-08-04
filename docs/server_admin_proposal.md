The current system for server administration - mtaserver.conf, acl.xml and the webadmin is confusing. We need a simple, unified interface that suits both normal server owners and those who rent servers.

The key aim of this proposal is to allow servers to be configured via the HTTP server and to make this the default route that new users use.

Tasks
-----

-   Allow mtaserver.conf can be reloaded at runtime.
-   Allow multiple mtaserver.conf files to be loaded, perhaps with each .conf file specifying the one to load \_before\_ it.
-   Allow acl.xml to be reloaded at runtime.
-   Allow multiple acl.xml to be loaded, specifying the file in the .conf file. Subsequent ACLs should overwrite existing ones - rights that previously were given should be denied. This will require some further thinking - if, say, banning was denied in the Everyone group in file 1, it shouldn't allow it to be granted to the Admin group in file 2.
-   Provide script functions for setting conf file settings in a particular file (presumably limited to those that are currently loaded), and a function for reloading a particular conf file. These should be ACL'd per config file.

Result
------

For most uses:

-   mtaserver.conf: references acl.xml as the xml to load
-   acl.xml

For server renters:

-   owner.conf: references owneracl.xml, sets player limit/name etc, specifies that mtaserver.conf should be loaded
-   owneracl.xml: prevents access to owner.conf
-   mtaserver.conf: specifies user settings, may specify a player limit, but this will be overwritten by the contents of owner.conf
-   acl.xml

Other tangental issues
----------------------

A better interface for setting resource settings would be convenient. Many resources are now using them.
