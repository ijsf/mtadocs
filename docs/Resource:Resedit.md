**resedit** is a server environment management extension for MTA. It allows you to remotely create and modify resources, mainly their scripts.

Getting Started
---------------

Writing scripts in resedit is very easy. It is designed to adapt to your favour. But before you start scripting away, let's take a look at the interface itself.

### menubar

The purpose of the **menubar** is to access important features in any viewing mode of the editor.

| Group   | Description                                                                                                                                                                                                                      |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| File    | Basic functionality to manage resources and files. For instance, you can open a new resource or delete scripts.                                                                                                                  |
| Options | Here are globally shared settings for all resedit sessions. You can change the feel and appearance of resedit, such as syntax highlighting. It is worth taking your time and browing through these settings!                     |
| Tools   | These are more advanced configurations and toolchains. If you are an experienced resedit user, you can modify it's settings through .xml management. In later versions I will include snippets for script editing convenience :) |
| View    | Under this category you find options based on interface management. Anything you apply here is temporary to your current resedit session.                                                                                        |
| ?       | In future releases you will find documentations here to guide you through resedit. Now there is just the **about** dialog.                                                                                                       |

### Filelist (left navigation)

The **filelist** is the quick-access listbox for scripts and resource files. A single click on a filename will execute the file for you. If you click on a script, a new scripting session will open. Clicking on other file-extensions will execute the appropriate standard-action for them. Entries are colored after file extensions for user friendlyness.

The **viewing mode** directly modifies the contents of this navigation. You can switch between **script** and **file** mode.

### Resource Settings (right navigation, top)

The tabpanel is made to give you a quick overview of the resource's settings. On the **General** tab you see the contents of the **meta.xml <info /> node** and basic commands for starting and stopping of the current resource. The **script** tab lets **add and remove scripts**.

### Functionlist (right navigation, bottom)

You can look up functions and their declaration in the **functionlist**. I am trying my best to keep the entries up-to-date.

### Editor Tabs

In the middle is the main development area for resedit extensions. By default, resedit keeps the **Notes** tab open. It has a non-syntax-highlighted editor which you can drop some notes in without having to open a script. Once you have selected some scripts in the **Filelist**, scripting sessions will open in new tabs. They will keep a direct connection with the server and listen to potencial changes to script files through different users.

A **Lua scripting editor** will behave the way you customized it in the **Preferences**. By default, the linebar and syntax-highlighting are enabled. If your mouse hovers over functionnames long enough, a hint with the function's info will appear. You can modify highlighting and hinting details using the **Advanced Configurations**.

Security
--------

resedit takes great care about server security. By default users can only edit scripts which they have **MTA ACL access** to. That means that guest accounts cannot view nor modify admin resources. Access to the resedit resource is always prohibited if not specially stated in the **access.xml**.

The access scheme is inheritance based. Moderators cannot access admin resources because they miss the “Admin” acl definition. That is why not even admins can access the **race** resource (raceACL definition). Resources can be seen as visitors to your server. A good ACL security will prevent harm to your resource environment. So if you correctly manage the ACL definitions, you do not have to use the **access.xml** file.

Addon documentation
-------------------

Read this section if you want to find out how to mod resedit. I allow you to change resedit's behaviour in any way.

### GUI elements

Starting from resedit 0.8.6 there are lots of **GUI script files**. They are extensions to the **dxElements** system and you can modify them. Usually they are pretty small (~100-400 lines) and easily understandable.

You must not edit **dxElements** itself if you do not have a license for it. If you want to buy it, contact me. Using it in your project without a valid license is not allowed.

### access.xml

This file contains general access settings for MTA. You should modify this file before running resedit to secure your server. Here is an example of what it could contain.

    <access>
        <default>
            <right object="editor.access" allow="true"></right>
            <right object="editor.objectManagement" allow="true"></right>
            <right object="editor.scriptLock" allow="true"></right>
            <right object="editor.createResource" allow="true"></right>
            <right object="editor.removeResource" allow="false"></right>
            <right object="controlPanel.access" allow="false"></right>
            <right object="controlPanel.requirePassword" allow="true"></right>
            <right object="resource.mauto*" allow="false"></right>
            <right object="resource.xs*" allow="false"></right>
            <right object="resource.xStunt" allow="false"></right>
            <right object="resource.attach" allow="false"></right>
            <right object="resource.qais*" allow="false"></right>
            <right object="resource.jesse*" allow="false"></right>
        </default>
        <aclgroup id="Moderator">
            <right object="controlPanel.access" allow="true"></right>
        </aclgroup>
        <account user="The_GTA">
            <right object="editor.access" allow="true"></right>
            <right object="editor.objectManagement" allow="true"></right>
            <right object="editor.scriptLock" allow="true"></right>
            <right object="editor.createResource" allow="true"></right>
            <right object="editor.removeResource" allow="true"></right>
            <right object="resource.*" allow="true"></right>
            <right object="controlPanel.access" allow="true"></right>
            <right object="controlPanel.requirePassword" allow="true"></right>
        </account>
        <account user="Remi-X">
            <right object="resource.mauto*" allow="true"></right>
            <right object="resource.xs*" allow="true"></right>
            <right object="resource.xStunt" allow="true"></right>
        </account>
        <account user="Qais">
            <right object="resource.attach" allow="true"></right>
            <right object="resource.qais*" allow="true"></right>
        </account>
        <account user="Jesseunit">
            <right object="resource.jesse*" allow="true"></right>
        </account>
    </access>

| Nodename | Description                                                                                        |
|----------|----------------------------------------------------------------------------------------------------|
| default  | Contains settings applied for guest accounts and accounts for which no **account** node was found. |
| account  | Special priviledges for a single account                                                           |
| aclgroup | Not supported yet. Planned feature ;)                                                              |
| right    | Grants a priviledge to the account.                                                                |

| Priviledge                   | Description                                                                                                                     |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| editor.access                | View the resedit GUI                                                                                                            |
| editor.objectManagement      | Modify MTA elements using object management                                                                                     |
| editor.scriptLock            | Can the user modify scripts?                                                                                                    |
| editor.createResource        | Can the user create resources?                                                                                                  |
| editor.removeResource        | Can the user remove resources?                                                                                                  |
| controlPanel.access          | TODO                                                                                                                            |
| controlPanel.requirePassword | TODO                                                                                                                            |
| resource.*\#name\#*          | Grants the user access to a resource. The \#name\# field is a **globmatch** so you can use the **\*** for wildcard definitions. |

[Category:Resource](/Category:Resource.md "wikilink")
