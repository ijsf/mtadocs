<lowercasetitle/>

Syntax
------

``` lua
void getXMLNodes( string xmlfilename, string nodename)
```

### Required Arguments

-   **xmlfilename**: The xml file name and path
-   **nodename**: Node name in xml file

### Optional Arguments

Code
----

<section name="Serverside/clientside" class="server/client" show="true">
``` lua
function getXMLNodes(xmlfile,nodename)
   local xml = xmlLoadFile(xmlfile)
   if xml then
      local ntable={}
      local a = 0
      while xmlFindChild(xml,nodename,a) do
         table.insert(ntable,a+1)
         ntable[a+1]={}
         local attrs = xmlNodeGetAttributes ( xmlFindChild(xml,nodename,a) )
         for name,value in pairs ( attrs ) do
            table.insert(ntable[a+1],name)
            ntable[a+1][name]=value
         end
         
         ntable[a+1]["nodevalue"]=xmlNodeGetValue(xmlFindChild(xml,nodename,a))
 
         a=a+1
      end
      return ntable
   else
      return {}
   end
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
``` lua
local aTeam = getXMLNodes("teams.xml","team")
for ka,vc in ipairs(aTeam) do
    outputDebugString(vc.tag)
end
```

</section>
XML&lt;teams.xml&gt;

``` xml
<teams>
<team tag="|OS|" />
<teams>
```

Author: NeoN

See Also
--------
