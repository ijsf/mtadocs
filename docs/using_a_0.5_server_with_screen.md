You finally have your brand new dedicated server, you upload the MTA server with FTP, you configure your config file and start the server.

![05-ssh-normal.jpg](/images/05-ssh-normal.jpg)

But then, disaster strikes. When you close your SSH connection, the server drops dead.

Well, at least you have gotten this far. Congratulations. The server closes when you close your session because the server is running on your current terminal. When your session closes the terminal closes and terminates the server. There are 2 ways to work around this problem.

Starting the server in background mode
--------------------------------------

Most command line programs have a small built-in help system that allows you to see options. You can see these by using the -? swith. For MTA that would be

     ./MTAServer -? 

The output will look like:

![05-SSH-Help.jpg](/images/05-ssh-help.jpg)

We need to run our server in the background, so:

![05-SSH-background.jpg](/images/05-ssh-background.jpg)

There we go, our server is running in the background. But what if we need to stop it? Well, we would first need to find the process ID number, after that we use the kill command to stop it:

![05-SSH-kill.jpg](/images/05-ssh-kill.jpg)

There we go!

Now method number 2:

Using screen
------------

A remote Linux terminal supports multiple virtual screens. This is to stop the user from creating multiple sessions. This is done by the “screen” command. For more information:

    man screen

We first need to start a virtual screen, therefore we type in “screen”. At first glance it will look like the screen has just cleared, but it hasn't. Now you can start the server and close the terminal.

![05-SSH-screen.jpg](/images/05-ssh-screen.jpg)

When you come back and log in again you can see that the server is still running on a different terminal:

![05-SSH-screen3.jpg](/images/05-ssh-screen3.jpg)

with the command

    screen -r

you can bring back your server and look at the output:

![05-SSH-creen2.jpg](/images/05-ssh-creen2.jpg)

If you have more then one screen running the command *screen -r* will bring up a list of all running screens. Every line starts with a pid (or process ID) for the running script. To know what scripts goes with what, you can use

    ps x

. To bring up the screen use

    screen -r pid

where pid is the corresponding process ID.

Links
-----

[Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
[Screen FAQ](http://www4.informatik.uni-erlangen.de/~weigert/screen-faq.html)
[Screen on GNU.org](http://www.gnu.org/software/screen/)

[Category:MTA 0.5](/docs/category:mta_0.5.md "wikilink") [Category:Historical](/docs/category:historical.md "wikilink")
