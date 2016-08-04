ACL Groups are groups that holds objects such as accounts, and resources which allows them to do some things depending on the permission the group has/holds.

(Referring to [ACL\#Default\_Groups](/docs/ACL#Default_Groups.md "wikilink"))

### Default Groups

MTA has provided some default groups with increasing permissions. These groups are:

-   **Everyone**
-   **Moderator**
-   **SuperModerator**
-   **Admin**
-   **Console** - This controls permissions of people who are using the console through **<object name="user.Console" />**
-   **RPC** - Remote Procedure Call. Specifically grants access to [callRemote](/docs/callRemote.md "wikilink") only and disables commands of default resources. Check the function for details.

To explain further, I will use the Everyone group as an example. By default it looks like this:

``` lua
    <group name="Everyone">
        <acl name="Default" />
        <object name="user.*" />
        <object name="resource.*" />
    </group>
```

You will first notice the acl name inside the group. It defines what permissions the group has. Users and resources in this group will have the permissions specified on the “Default” acl name list. *Note: You will notice this group is special, in that it includes every user and resource by using a **wildcard (\*)** where the user or resource name would be.*

Now, scroll further down the ACL and you will see the **<acl name="Default" />** listing. Note I have trimmed this list dramatically due to its length.

``` lua
    <acl name="Default">
        <right name="command.start" access="false" />
        <right name="command.stop" access="false" />
        <right name="command.stopall" access="false" />
        ...etc etc...
        <right name="function.executeCommandHandler" access="false" />
        <right name="function.setPlayerMuted" access="false" />
        <right name="function.restartResource" access="false" />
        ...etc etc...
        <right name="general.adminpanel" access="false" />
        <right name="general.tab_players" access="false" />
        <right name="general.tab_resources" access="false" />
        ...etc etc...
        <right name="command.freeze" access="false" />
        <right name="command.shout" access="false" />
        <right name="command.spectate" access="false" />
        ...etc etc...
    </acl>
```

\***Function** entries are MTA scripting functions. For example, if a resource needed to use restartResource and was only in the 'Everyone' group (with the 'Default' list), it would be denied access to restartResource and fail to work correctly.

-   **Commands** are created when a resource uses [addCommandHandler](/docs/addCommandHandler.md "wikilink"). An example would be typing **/createvehicle \[vehicle\]** in the chatbox for the freeroam resource. This controls whether users in the group using this ACL can use the command. *Note: commands have no effect on resources within the group. Commands are only related to users.*
    -   *General is a custom right name group created by the admin resource but it works on the same principles. The script works with them by using [hasObjectPermissionTo](/docs/hasObjectPermissionTo.md "wikilink")*

You will notice some groups such as admin have multiple **<acl name="" />** nodes. An example is the admin group:

``` lua
    <group name="Admin">
        <acl name="Moderator" />
        <acl name="SuperModerator" />
        <acl name="Admin" />
        <acl name="RPC" />
        <object name="resource.admin" />
        <object name="resource.webadmin" />
        <object name="user.Ransom" />
    </group>
```

This gives all the permissions defined in each **<acl name="" />** node in order of listing. So for example, the admin group makes sure all the permissions are given to admins by using all the lists. If there are any conflicts, the lowest entry wins. For example, pretend these 2 acls were in a group in the following order:

**1.** **<acl name="Default">** sets <right name="general.ModifyOtherObjects" access="false" /> <br\> **2.** **<acl name="Admin">** sets <right name="general.ModifyOtherObjects" access="true" /> <br\> **3.** For all users and resources in group admin: <right name="general.ModifyOtherObjects" access="true" /><br\> <br\>
