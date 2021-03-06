This is a scripting tutorial teaching you how to create a private messaging system in your server. It was originally created on Thursday November 24th, 2011 at 6:32pm (UTC) by qaisjp for MTA:SA 1.1. The original code was tested on the day of original creation, but it was thoroughly revamped since then.

Creating the basic resource
---------------------------

Creating your resource is one of the important parts of the tutorial. In Multi Theft Auto, resources are described as sets of scripts; there are many different types of resources but I won't go into detail of that because it is outside the scope of my tutorial. I will not teach the details about **meta.xml** files, but I will walk you through it. For more detailed information on resources and how to create one, follow the [Resources](/docs/resources.md "wikilink") tutorial.

First, you'll need to go to your resources directory. For those running a server from the “HOST GAME” option at the Main Menu, the resources directory will be at *C:/Program Files/MTA San Andreas 1.1/server/mods/deathmatch/resources/*. This path will slightly vary depending on your install location, game version and system architecture - regardless of these three factors it should be pretty easy to find your resource directory. Once you've found it you should create a new directory *inside* the “resources” folder called “pm-system”, this will be our resource. From now on you'll be working on the system inside this folder

Inside our working directory, “pm-system”, create a *meta.xml* and a *server.lua* file. The **meta** file is an XML file which tells Multi Theft Auto which scripts to run and in which order; we only need it to run *server.lua*.

<section name="meta.xml" class="server" show="true">
XML is another language, so I won't teach you much about it. But to learn more about the meta.xml file, visit [this page](/docs/meta.xml.md "wikilink"). So type the following code into the file.

``` xml
<meta>
    <info author="qaisjp" version="1.0" name="PM System" description="Introduces /pm into MTA" type="script" />
    <script src="server.lua" type="server" />
</meta>
```

</section>
And now thats the meta file finished, onto the real script!

Creating the command handler
----------------------------

Creating command handlers are the way to creating commands in MTA, you won't have to monitor chat input and manually separate text - it's all nicely put into one nice function. First we have to create a function, and then create a command which will bind itself to the function. To do this we use [addCommandHandler](/docs/addcommandhandler.md "wikilink"), so let's start off with this code:

``` lua
-- Create the function
function pmHandler()
end

-- Create the command
addCommandHandler("pm", pmHandler)
```

What happens here is that on the second line we start creating a function, on the third line we stop creating the function. Then on the last line we call (execute, start, ask - whatever helps you understand) the [addCommandHandler](/docs/addcommandhandler.md "wikilink") function. The first argument is “pm”, this tells the function that the command we're making will react to the input of "/pm" in the chatbox. The second argument is *pmHandler*, this wasn't wrapped in quotation marks. If you noticed on line 2 that we created a function called *pmHandler*, you can guess that this tells addCommandHandler to bind that function to the command. Testing this right now won't show anything, so I won't teach you how to test it out yet.

Lets have some arguments...
---------------------------

In between the brackets (it's actually called parentheses) on line 2 are the arguments that are passed to the function - just like how we passed arguments to addCommandHandler, arguments are caught here. There are two default arguments, and then all the arguments after that are an unknown number of strings. The first argument is the element of the player who typed the command, we'll ignore the second argument because we don't need it. The third argument onwards are the arguments that are passed to the command, so if you typed "/pm user I like MTASA" this is how it would read it as:

``` lua
function pmHandler(player, cmd, target, word1, word2, word3)
    -- outputChatBox is a function we call to output content to the chatbox.
    outputChatBox(target .. word1 .. word2 .. word3)
end
addCommandHandler("pm", pmHandler)
```

So typing that would print out something like **userIlikeMTASA** to the chatbox for everyone. Obviously the first argument to the function and command will be the name of the person we want to send the **private** (not public!) message to. So we need to check if the player exists or not.

Hitting your target
-------------------

We won't check if a player exists, that's too troublesome. Instead we'll resort to a simple function that we know will return [nil](/docs/nil.md "wikilink") (nothing). When functions return something, it's like when you ask someone a question and they reply back with a definite answer when they think and answer your question or reply to your order. “That is false, sir”, “That is true, sir!” and “Mission failed, sir!”. We'll be using [getPlayerFromName](/docs/getplayerfromname.md "wikilink"). This function takes one argument, the name of the player we want and it returns to kinds of values: [nil](/docs/nil.md "wikilink") (nothing) and a [Player](/docs/player.md "wikilink") [element](/docs/element.md "wikilink"). It will return nil if it couldn't find a player with that exact name (ignoring capital letters) or it will return a player element if it could find a match. So let's add that to our code:

``` lua
function pmHandler(player, cmd, target, word1, word2, word3)
    local recipient = getPlayerFromName(target) -- recipient is another word for "receiver"
```

Slow down! Here we set a variable to what “getPlayerFromName” returned. It's like assigning a door a name, the door can contain a player or it can contain nothing - but you can always remember what door it is by the name it is assigned to (the name which is written on the door). This means that *recipient* will be the value of whatever getPlayerFromName returns.

We have to check if it returns nil or a player element, since nil is virtually nothing and all it should return is a player element, so we can send him the message. Time to carry on my code.

``` lua
function pmHandler(player, cmd, target, word1, word2, word3)
    local recipient = getPlayerFromName(target) -- recipient is another word for "receiver"
    if recipient then -- if recipient exists then...
        local recipientName = getPlayerName(recipient)
```

Here we are getting the name of the recipient... but you might be thinking “but if the player already knows it why are we double checking?”. The reason we are getting the name of the player again is because getPlayerFromName is case insensitive, meaning it ignores the difference between “The\_GTA” and “the\_gta”. We'll be telling the PM creator, the user, who he PM'ed later so we want the name to show up correctly and not with capital letters missing or in the wrong place. We need to tell the player that the player doesn't exist if it doesn't, just so he knows that /pm works and that it failed. Read on.

``` lua
function pmHandler(player, cmd, target, word1, word2, word3)
    local recipient = getPlayerFromName(target) -- recipient is another word for "receiver"
    if recipient then -- if recipient exists then...
        local recipientName = getPlayerName(recipient)
    else -- but what if recipient doesn't exist? then...
        -- This tells "recipient" that he's made a mistake, in red.
        outputChatBox("Sorry, we don't know a person called " .. target, player, 255, 0, 0)
    end -- there's no more possibilities, so close off this scope of questioning.
end
```

If you want to try and test it out on yourself, save this (it should be in server.lua and you should've been editing in that file anyway) and (re)start the resource. Typing the name of someone who isn't on the server should make that error appear, but typing your name (or someone who is on the server) should appear to do nothing... for now.

Outputting Messages
-------------------

Now we've sorted out error handling - making sure there is a person to PM to and telling the user he's made a mistake - we can start on the part that tells both users that he/she's sent/received a PM. We will use similar code to the error handling output code, we'll be using hex here too. I won't explain much about hex because it's fairly simple, but Google is your friend for all of eternity (or until the NSA decides to take over the world).

``` lua
function pmHandler(player, cmd, target, word1, word2, word3)
    local recipient = getPlayerFromName(target)
    if recipient then
        local recipientName = getPlayerName(recipient)
        local playerName = getPlayerName(player) -- also get the name of the player, to tell the recipient who sent him the pm

        -- Tell the author he's sent a message
        outputChatBox("[PM > " .. recipientName .. "]: #FFFFFF " .. word1 .. " " .. word2 .. " " .. word3, player, 255, 255, 0, true)

        -- Tell the recipient he's received a message
        outputChatBox("[PM < " .. playerName .. "]: #FFFFFF " .. word1 .. " " .. word2 .. " " .. word3, recipient, 255, 255, 0, true)
    else
        outputChatBox("Sorry, we don't know a person called" .. target, player, 255, 0, 0)
    end
end
```

Make sure you read the code, I've explained it in here. Go on, test your message!

Second class citizen
--------------------

You may have noticed that the PM messages don't go beyond three words. If you're daring you might've tried to extend it to a couple of more words. Don't worry, there's an easy “fix” - and it doesn't involve copying the same variables over and over and over and over and over and over and over and ov.. (I am getting carried away here, aren't I?) .. er again. The wonderful "...", you should already know ".." concatenates (attaches/combines/merges/appends) two variables but "..." is something different. It's a special kind of variable and it cannot be set anywhere except in function arguments, it has to be the last argument and it can only be manipulated when wrapped in a table (in the latest Lua). Tables are rather simple and integral features of Lua but it can be challenging for newcomers. I won't explain this third-world-variable much because you may or may not understand tables correctly themselves.

First we'll remove *word1*, *word2* and *word3* and replace it with *...*

``` lua
function pmHandler(player, cmd, target, ...)
    local recipient = getPlayerFromName(target)
    if recipient then
        local recipientName = getPlayerName(recipient)
        local playerName = getPlayerName(player)
        outputChatBox("[PM > " .. recipientName .. "]: #FFFFFF " .. , player, 255, 255, 0, true)
        outputChatBox("[PM < " .. playerName .. "]: #FFFFFF " .. , recipient, 255, 255, 0, true)
    else
        outputChatBox("Sorry, we don't know a person called" .. target, player, 255, 0, 0)
    end
end
```

Now we will wrap *...* in a table for it to be manipulated and accessed.

``` lua
function pmHandler(player, cmd, target, ...)
    local recipient = getPlayerFromName(target)
    if recipient then
        local message = {...}
        local recipientName = getPlayerName(recipient)
        local playerName = getPlayerName(player)
        outputChatBox("[PM > " .. recipientName .. "]: #FFFFFF " .. , player, 255, 255, 0, true)
        outputChatBox("[PM < " .. playerName .. "]: #FFFFFF " .. , recipient, 255, 255, 0, true)
    else
        outputChatBox("Sorry, we don't know a person called" .. target, player, 255, 0, 0)
    end
end
```

With this, we can access each following argument like message\[index\]. This means that if we did "/pm qaisjp I like MTA a lot..." *message* would be structured like this:

-   message\[1\] = **I**
-   message\[2\] = **like**
-   message\[3\] = **MTA**
-   message\[4\] = **a**
-   message\[5\] = **lot...**

If we wanted to concatenate all these variables, right up to the last one, together seperating it by a space we would use the “table.concat” function. table.concat is a default lua function which concatenates all the items of a table in order with a separator. Here we use table.concat({...}, " "), so we concatenate all the arguments with the space being a separator. And of course, add those changes to the outputChatBox code.

``` lua
function pmHandler(player, cmd, target, ...)
    local recipient = getPlayerFromName(target)
    if recipient then
        local message = table.concat({...}, " ") 
        local recipientName = getPlayerName(recipient)
        local playerName = getPlayerName(player)
        outputChatBox("[PM > " .. recipientName .. "]: #FFFFFF " .. message, player, 255, 255, 0, true)
        outputChatBox("[PM < " .. playerName .. "]: #FFFFFF " .. message, recipient, 255, 255, 0, true)
    else
        outputChatBox("Sorry, we don't know a person called" .. target, player, 255, 0, 0)
    end
end
```

Conclusion
----------

And that is it! You've learn a bit about tables, a bit about arguments, a bit about that third-world variable, and how to create a PM system. For those that would like to see the final code, collapse the code below. PM system is hardly the hardest thing you can create in MTA:SA, it's one of the easiest things. But it may be a milestone for you, so make sure you tell me how you did on this tutorial at [official topic for this tutorial](http://forum.mtasa.com/viewtopic.php?t=37395%7Cthe).

<section name="server.lua" class="server" show="false">
``` lua
function pmHandler(player, cmd, target, ...)
    local recipient = getPlayerFromName(target)
    if recipient then
        local message = table.concat({...}, " ") 
        local recipientName = getPlayerName(recipient)
        local playerName = getPlayerName(player)
        outputChatBox("[PM > " .. recipientName .. "]: #FFFFFF " .. message, player, 255, 255, 0, true)
        outputChatBox("[PM < " .. playerName .. "]: #FFFFFF " .. message, recipient, 255, 255, 0, true)
    else
        outputChatBox("Sorry, we don't know a person called" .. recipientName, recipient, 255, 0, 0)
    end
end
addCommandHandler("pm", pmHandler)
```

</section>
[Category:Tutorials](/docs/category-tutorials.md "wikilink")
