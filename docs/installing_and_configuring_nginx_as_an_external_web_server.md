Internal vs External
--------------------

The MTA:SA server comes with a built-in 'internal' HTTP server which clients use to automatically download resource files. It is only a basic HTTP server which does not support compression or multiple client connections. By adding an external HTTP server such as **nginx** or **lighttpd**, resource download speed can be increased and bandwidth usage (and player waiting time) decreased. Note that the external HTTP server can be on the same machine as the MTA server.

nginx vs Apache
---------------

We recommend nginx or lighttpd as they are better suited to handle the hundreds of file requests that MTA:SA clients will generate. Apache can be used, but will require settings tweaking and the mtasever.conf setting &lt;**httpmaxconnectionsperclient**&gt; may have to be reduced to prevent timeouts.

The following guide is for installing and configuring nginx solely for MTA:SA. It assumes:

-   You are not already using nginx for other web sites on your server.
-   MTA:SA server is installed on the same server.
-   You are using Debian 7 (but should work on other distributions in a similar way.)

Installing nginx:
-----------------

Update system:

`apt-get update`
`apt-get upgrade`

Install nginx:

`apt-get install nginx`

Ensure nginx is not running:

`/etc/init.d/nginx stop`

Configuring nginx:
------------------

#### Edit: /etc/nginx/sites-enabled/mta-server1

In the directory **/etc/nginx/sites-enabled/** create a file called **mta-server1** with the following content:

`server {`
`    listen 20080;`
`    root /PATH_TO_MTA_SERVER/mods/deathmatch/resource-cache/http-client-files;`
`    server_name localhost;`
`    access_log off;`
`}`

**\*\*Important\*\*: Change PATH\_TO\_MTA\_SERVER to the actual absolute path of your MTA:SA server install directory**

#### Edit: /etc/nginx/nginx.conf

At the top of the file, add this line to increase the max number of files that can be opened:

`worker_rlimit_nofile 5000;`

Find the **'worker\_connections**' line and change it to this:

`worker_connections 5000;`

Find the **'gzip**' settings and make sure gzip is on:

`gzip on;`

and **'gzip\_types**' is set for any file type:

`gzip_types *;`

Testing nginx:
--------------

Start nginx:

`/etc/init.d/nginx start`

##### Test \#1

Open your internet browser, and try this address: **http://YOUR\_SERVER\_IP:20080/admin/client/admin\_ACL.lua**
If prompted to download a file - SUCCESS!

##### Test \#2

To test the compression is working, go here: <http://www.whatsmyip.org/http-compression-test/> and enter **http://YOUR\_SERVER\_IP:20080/admin/client/admin\_ACL.lua** in the white box and press 'Test'.
If green tick - SUCCESS!

Configure MTA:SA server:
------------------------

#### Edit mtaserver.conf

Set **httpdownloadurl** to be like this:

`   `<httpdownloadurl>**`http://YOUR_SERVER_IP:20080`**</httpdownloadurl>

And start MTA:SA server.
