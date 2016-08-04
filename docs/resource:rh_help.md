This is intended as a replacement for the standard help manager resource. It looks for help.xml files in running resources and displays the text.

This resource does not support the GUI customization from helpmanager, but does offer more flexibility when dealing with help.xml files. This resource will let you provide your own titles (instead of using resource names only) and a set order in which your “chapters” or help resources will appear.

Download
--------

The resource can be found on the resource center. [Resource page](http://community.mtasa.com/index.html?p=resources&s=details&id=540)

Usage
-----

### Scripters

To add a help entry/chapter to a resource, include the following line in its meta.xml.

``` xml
<config src="help.xml" type="client"/>
```

This will make sure the help.xml file is downloaded and accessible.

The actual help chapter must be entered in this help.xml file. A normal help.xml file syntax looks like this:

``` xml
<help title="My title" ordering="42">
Help text here
</help>
```

The part inside the actual tag (“Help text here”) is what will be displayed in the text box. The title attribute is what will be displayed for this chapter in the list. The ordering attribute “sorts” the chapters so you can have them in a certain order. (Ascending, that is, higher numbers go lower in the list.) Both attributes are optional. If title is not given, then the list item will show up as the resource name. If ordering is not given, it will be decided by the order in which the resources are started and/or restarted.

rh\_help is backwards-compatible with helpmanager, which means you don't have to do anything more than running this resource (and disabling the old one) to start using it. It can tackle the old help.xml layout just fine.

### Players

**F9**: toggles the help window.

**/gamehelp**: also toggles the help window. :)

**Note:** both the key and the command can be changed to something else in the script, although this is not recommended for two reasons. It will make things harder for players who are used to these fairly standardized ways of opening a help GUI, and unless you rename the script file (I didn't really care to bother putting in a server-side file just for settings when they ideally shouldn't be changed to begin with...) clients will need to download it again on other servers, and AGAIN when they returns to yours.
