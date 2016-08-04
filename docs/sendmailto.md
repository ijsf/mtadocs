<lowercasetitle/>

This function allows you to send a mail with a php system You must include the “MTASDK” in your PHP file. (https://wiki.multitheftauto.com/wiki/PHP\_SDK)

Syntax
------

``` lua
string sendMailTo( string mail, string sender, string headertext, string text)
```

Required Arguments
------------------

-   **text:** The text of the e-mail is in the.

Optional Arguments
------------------

-   **mail:** Here, the recipient is defined.
-   **sender:** Here, the sender must be entered that sent the e-mail.
-   **headertext:** Here the subject text needs to go, which it is e-mail in the subject line.

Code
----

    function sendMailTo ( mail, sender, headertext, text )

        callRemote ( "http://www.example.com/send.php", EMailAccepted, mail, sender, headertext, text )

    end

    function EMailAccepted ()

        outputDebugString ( "E-Mail was succesfully sended." )

    end

**PHP:** You must create a send.php file, then then convert to UTF-8 on your FTP upload.

``` php
<?php 
    
    include ( "mta_sdk.php" );
    $input = mta::getInput();
    
    mail($input[0], $input[2], $input[3], "From: ".$input[1]."\n" . "Content-Type: text/html; charset=iso-8859-1\n"); 
?>
```

Example
-------

<section name="Server" class="server" show="true">
    function MailText ( player, cmd, headertext, ... )
        local text = table.concat ( {...}, " " )
        if text then
            
            sendMailTo ( "yourmail@example.com", "sendermail@example.com", headertext, text )
            
        end
        
    end
    addCommandHandler ( "sendmail", MailText )

</section>
Author: SuperHomie(me)
