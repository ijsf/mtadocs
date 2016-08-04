A quick tutorial on how to get admin rights and install admin resource.

<section name="MTA 1.0.0 and lower" class="server" show="false">
**Note:** Since mta 1.0.5 the accounts.xml file has been removed and replaced by sqlite.

At first, open the **accounts.xml** file located in **server\\mods\\deathmatch\\** and add a line with your account details, like on the following example.

![admin\_accounts.png](/images/admin_accounts.png)

</section>
To add an account in **MTA ** use the following command in the server

**Note:** The server needs to run for this action

    addaccount <username> <password>

**Note:** Server should not be running when you are editing the acl file below

Then you open the **acl.xml** file located in the same folder and add yourself as an object to the Admin group by using the 'user.\*' syntax, where \* would be your account name.

![admin\_acl.png](/images/admin_acl.png)

Now open your **mtaserver.conf** file and scroll to the bottom, make sure the admin resource is added to the ones that start with the server (note: protected=“1” means that it can not be stopped).

![admin\_mtaserver.png](/images/admin_mtaserver.png)

Now that you're done with server files, you can finally start it. Connect to the server itself and login with your account details: use 'login \[username\] <password>'. If it tells you to press 'p' you have done everything right, congratulations! If not, do this from the very beginning. [Category:Scripting Concepts](/docs/category:scripting_concepts.md "wikilink")

[it:<Resource:Admin>](/docs/it:resource:admin.md "wikilink") [ru:<Resource:Admin>](/docs/ru:resource:admin.md "wikilink")
