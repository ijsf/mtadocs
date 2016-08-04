**ACL** or **Access Control List** is a set of rights grouped together to create a list, they are defined in the [ACL.xml](/Access_Control_List.md "wikilink") file as <acl> nodes. These ACLs can then be added to certain [ACL Groups](/ACL_Group.md "wikilink") to grant or deny these groups specified permissions or acces to server scripting functions defined in the ACL. Example of an ACL:

    <acl name="Example">
            <right name="general.ModifyOtherObjects" access="true" />
            <right name="function.startResource" access="true" />
            <right name="function.stopResource" access="true" />
            <right name="function.shutdown" access="false" />
            <right name="command.shutdown" access="false" />
    </acl>

This creates ACL called *Example* and gives resources access to start/stop resources and modify other resources but denies access to shutting down the server. Players that are in group using this ACL will be denied access to *shutdown* command.

Related scripting functions
---------------------------

-   [aclCreate](/aclCreate.md "wikilink")
-   [aclDestroy](/aclDestroy.md "wikilink")
-   [aclGet](/aclGet.md "wikilink")
-   [aclGetName](/aclGetName.md "wikilink")
-   [aclGetRight](/aclGetRight.md "wikilink")
-   [aclSetRight](/aclSetRight.md "wikilink")
-   [aclList](/aclList.md "wikilink")
-   [aclListRights](/aclListRights.md "wikilink")
-   [aclRemoveRight](/aclRemoveRight.md "wikilink")

[Category:Scripting Concepts](/Category:Scripting_Concepts.md "wikilink")
