One important feature in MTA:SA is the ability to script customized GUI (Graphic User Interface). The GUI consists of windows, button, edit boxes, check boxes... Almost every standard form components in graphical environments. They can be displayed while the user is in game, and used for inputs and outputs in place of traditional commands.

[thumb|Admin Console GUI](/docs/image-admingui.png.md "wikilink")

A tutorial to make a login window
---------------------------------

In this tutorial we'll make a simple login window, with two input boxes and a button. The window appears when the player joins the game, and once the button is clicked, the player is spawned. The tutorial will continue the gamemode we made in [Introduction to Scripting](/docs/scripting_introduction.md "wikilink") *(If you have used the [Introduction to Scripting](/docs/scripting_introduction.md "wikilink"), you will need to remove or comment the [spawnPlayer](/docs/spawnplayer.md "wikilink") line in the “joinHandler” function in your code, as we will be replacing it with a gui alternative in this tutorial)*. We'll also take a look at client-side scripting.

### Draw the window

All the GUI must be made client side. It is also a good practice to keep all the client scripts in a separate folder.

Browse to /Your MTA Server/mods/deathmatch/resources/myserver/ directory, and create a folder named “client”. Under /client/ directory, create a text file and name it “gui.lua”.

In this file we will write a funtion that draws the window. To create a window we will use [guiCreateWindow](/docs/guicreatewindow.md "wikilink"):

``` lua
function createLoginWindow()
    -- define the X and Y positions of the window
    local X = 0.375
    local Y = 0.375
    -- define the width and height of the window
    local Width = 0.25
    local Height = 0.25
    -- create the window and save its element value into the variable 'wdwLogin'
    -- click on the function's name to read its documentation
    wdwLogin = guiCreateWindow(X, Y, Width, Height, "Please Log In", true)
end
```

### Relative and Absolute

Note that the final argument passed to guiCreateWindow in the above example is *true*. This indicates that the coordinates and dimensions of the window are **relative**, meaning they are a *percentage* of the total screen size. This means that if the far left side of the screen is 0, and the far right is 1, an X position of 0.5 would represent the centre point of the screen. Similarly, if the top of the screen is 0 and the bottom is 1, a Y position of 0.2 would be 20% of the way down the screen. The same principles apply to both Width and Height as well (with a Width value of 0.5 meaning the window will be half as wide as the screen).

The alternative to using relative values is using **absolute** (by passing *false* instead of true to guiCreateWindow). Absolute values are calculated as the total number of pixels from the top-left corner of the parent (if no gui element parent is specified, the parent is the screen itself). If we assume a screen resolution of 1920x1200, the far left side of the screen being 0 pixels and the far right being 1920 pixels, an X position of 960 will represent the centre point of the screen. Similarly, if the top of the screen is 0 pixels and the bottom is 1200, a Y position of 20 would be 20 pixels down from the top of the screen. The same principles apply to both Width and Height as well (with a Width value of 50 meaning the window will be 50 pixels wide). *You can use [guiGetScreenSize](/docs/guigetscreensize.md "wikilink") and a little maths to calculate certain absolute positions.*

The differences between using relative and absolute values is quite simple; gui created using absolute values will always remain exactly the same pixel size and position, while gui created using relative values will always be a percentage of its parent's size.

Absolute is generally easier to maintain when editing code by hand, however your choice of type depends on the situation you are using it for.

For the purposes of this introduction we will be using relative values.

### Adding the components

Next, we'll add the text labels (saying “username:” and “password:”), edit boxes (for entering your data) and a button to log in.

To create buttons we use [guiCreateButton](/docs/guicreatebutton.md "wikilink") and to create edit boxes use [guiCreateEdit](/docs/guicreateedit.md "wikilink"):

**Note that we are now writing more code for our existing 'createLoginWindow' function. This is not a new function and is meant to replace what you already have.**

``` lua
function createLoginWindow()
    local X = 0.375
    local Y = 0.375
    local Width = 0.25
    local Height = 0.25
    wdwLogin = guiCreateWindow(X, Y, Width, Height, "Please Log In", true)
    
    -- define new X and Y positions for the first label
    X = 0.0825
    Y = 0.2
    -- define new Width and Height values for the first label
    Width = 0.25
    Height = 0.25
    -- create the first label, note the final argument passed is 'wdwLogin' meaning the window
    -- we created above is the parent of this label (so all the position and size values are now relative to the position of that window)
    guiCreateLabel(X, Y, Width, Height, "Username", true, wdwLogin)
    -- alter the Y value, so the second label is slightly below the first
    Y = 0.5
    guiCreateLabel(X, Y, Width, Height, "Password", true, wdwLogin)
    

    X = 0.415
    Y = 0.2
    Width = 0.5
    Height = 0.15
    edtUser = guiCreateEdit(X, Y, Width, Height, "", true, wdwLogin)
    Y = 0.5
    edtPass = guiCreateEdit(X, Y, Width, Height, "", true, wdwLogin)
    -- set the maximum character length for the username and password fields to 50
    guiEditSetMaxLength(edtUser, 50)
    guiEditSetMaxLength(edtPass, 50)
    
    X = 0.415
    Y = 0.7
    Width = 0.25
    Height = 0.2
    btnLogin = guiCreateButton(X, Y, Width, Height, "Log In", true, wdwLogin)
    
    -- make the window invisible
    guiSetVisible(wdwLogin, false)
end
```

Note that every GUI component created is a child of the window, this is done by specifying the parent element (wdwLogin, in this case) when creating the component.

This is very useful because not only does it mean that all the components are attached to the window and will move with it, but also that any changes done to the parent window will be applied down the tree to these child components. For example, we can now hide all of the GUI we just created by simply hiding the window:

``` lua
guiSetVisible(wdwLogin, false) --hides all the GUI we made so we can show them to the player at the appropriate moment. 
```

### Using the function we wrote

The createLoginWindow function is now complete, but it won't do anything until we call it. It is recommended to create all GUI when the client resource starts, hide them, and show them to the player later when needed. Therefore, we'll write an event handler for "[onClientResourceStart](/docs/onclientresourcestart.md "wikilink")" to create the window:

``` lua
-- attach the event handler to the root element of the resource
-- this means it will only trigger when its own resource is started
addEventHandler("onClientResourceStart", getResourceRootElement(), 
    function ()
        createLoginWindow()
    end
)   
```

As this is a log in window, we now need to show the window when the player joins the game. This can be done using the same event, "[onClientResourceStart](/docs/onclientresourcestart.md "wikilink")", so we can modify the above code to include showing the window:

**Note that we are now writing more code for our existing 'onClientResourceStart' handler. This is not a new event handler and is meant to replace what you already have.**

``` lua
addEventHandler("onClientResourceStart", getResourceRootElement(), 
    function ()
        -- create the log in window and its components
        createLoginWindow()

        -- output a brief welcome message to the player
                outputChatBox("Welcome to My MTA:SA Server, please log in.")

        -- if the GUI was successfully created, then show the GUI to the player
            if (wdwLogin ~= nil) then
            guiSetVisible(wdwLogin, true)
        else
            -- if the GUI hasnt been properly created, tell the player
            outputChatBox("An unexpected error has occurred and the log in GUI has not been created.")
            end 

        -- enable the players cursor (so they can select and click on the components)
            showCursor(true)
        -- set the input focus onto the GUI, allowing players (for example) to press 'T' without the chatbox opening
            guiSetInputEnabled(true)
    end
)   
```

Note that we have a simple security check before making the window visible, so in the unlikely event that the window has not been created, meaning wdwLogin is not a valid element, we don't get an error and just inform the player what has happened. In the next step, we will create the button functionality for the log in button.

Scripting the button
--------------------

Now that we have created our GUI and shown it to the player, we need to make it work.

### Detecting the click

When the player clicks on any part of the GUI, the event "[onClientGUIClick](/docs/onclientguiclick.md "wikilink")" will be triggered for the GUI component you clicked on. This allows us to easily detect any clicks on the GUI elements we want to use. For example, we can attach the event to the btnLogin button to catch any clicks on it:

``` lua
-- attach the event onClientGUIClick to btnLogin and set it to trigger the 'clientSubmitLogin' function
addEventHandler("onClientGUIClick", btnLogin, clientSubmitLogin, false)
```

**Note the final argument passed is “false”. This indicates that the event will only trigger directly on btnLogin, not if the event has propagated up or down the tree. Setting this to “true” while attaching to gui elements will mean that clicking on any element in the same branch will trigger this event.**

This line of code can now be added inside the createLoginWindow function. It is a common mistake to try and attach events to non-existant GUI elements, so make sure you always attach your events **after** the gui element (in this case, the button) has been created:

**Note that we are now writing more code for our existing 'createLoginWindow' function.**

``` lua
function createLoginWindow()
    -- create all our GUI elements
    ...

    -- now add our onClientGUIClick event to the button we just created
    addEventHandler("onClientGUIClick", btnLogin, clientSubmitLogin, false)
```

### Managing the click

Now that we can detect when the player clicks on the button, we need to write code to manage what happens when they do. In our [onClientGUIClick](/docs/onclientguiclick.md "wikilink") event handle, we told it to call the function clientSubmitLogin whenever btnLogin is clicked. Therefore, we can now use the function clientSubmitLogin to control what happens when the button is clicked:

``` lua
-- create the function and define the 'button' and 'state' parameters
-- (these are passed automatically by onClientGUIClick)
function clientSubmitLogin(button,state)
    -- if our login button was clicked with the left mouse button, and the state of the mouse button is up
    if button == "left" and state == "up" then
        -- move the input focus back onto the game (allowing players to move around, open the chatbox, etc)
        guiSetInputEnabled(false)
        -- hide the window and all the components
        guiSetVisible(wdwLogin, false)
        -- hide the mouse cursor
        showCursor(false)
    end
end
```

Now, when the button is clicked, the window will be hidden and all controls will be returned to the player. Next, we will tell the server to allow the player to spawn.

### Triggering the server

Triggering the server can be done using [triggerServerEvent](/docs/triggerserverevent.md "wikilink"). This allows you to trigger a specified event on the server from the client. The same can be done in reverse using [triggerClientEvent](/docs/triggerclientevent.md "wikilink"). Here, we use the [triggerServerEvent](/docs/triggerserverevent.md "wikilink") function to call our own custom event on the server, named “submitLogin”, which will then control the spawning of the player serverside.

**Note that we are now writing more code for our existing 'clientSubmitLogin' function. This is not a new function and is meant to replace what you already have.**

``` lua
function clientSubmitLogin(button,state)
    if button == "left" and state == "up" then
        -- get the text entered in the 'username' field
        local username = guiGetText(edtUser)
        -- get the text entered in the 'password' field
        local password = guiGetText(edtPass)

        -- if the username and password both exist
        if username and password then
            -- trigger the server event 'submitLogin' and pass the username and password to it
            triggerServerEvent("submitLogin", getRootElement(), username, password)

            -- hide the gui, hide the cursor and return control to the player
            guiSetInputEnabled(false)
            guiSetVisible(wdwLogin, false)
            showCursor(false)
        else
            -- otherwise, output a message to the player, do not trigger the server
            -- and do not hide the gui
            outputChatBox("Please enter a username and password.")
        end
    end
end
```

### Creating the serverside event

At this point we now have all the code needed on the client side, so open up your serverside 'script.lua' file (from the [Introduction to Scripting](/docs/scripting_introduction.md "wikilink")) or another suitable serverside file to work with.

On the server side, recall that we are spawning the player as soon as they login. So, first of all, we will need to define the custom event that we used before on the client. This can be done using [addEvent](/docs/addevent.md "wikilink") and [addEventHandler](/docs/addeventhandler.md "wikilink").

``` lua
-- create our loginHandler function, with username and password parameters (passed from the client gui)
function loginHandler(username,password)

end

-- define our custom event, and allow it to be triggered from the client ('true')
addEvent("submitLogin",true)
-- add an event handler so that when submitLogin is triggered, the function loginHandler is called
addEventHandler("submitLogin",root,loginHandler)
```

### Logging in

Now we have a function that is called through the custom event 'submitLogin', we can start to work on logging in and spawning the player, using our 'loginHandler' function:

``` lua
function loginHandler(username,password)
    -- check that the username and password are correct
    if username == "user" and password == "apple" then
        -- the player has successfully logged in, so spawn them
        if (client) then
            spawnPlayer(client, 1959.55, -1714.46, 10)
            fadeCamera(client, true)
                        setCameraTarget(client, client)
            outputChatBox("Welcome to My Server.", client)
        end
    else
        -- if the username or password are not correct, output a message to the player
        outputChatBox("Invalid username and password. Please re-connect and try again.",client)
        end         
end

addEvent("submitLogin",true)
addEventHandler("submitLogin",root,loginHandler)
```

**For the purposes of this tutorial, a very basic username and password system is shown. For a more comprehensive alternative, you can use the Account System or a MySQL database.**

Also note the use of the variable “client”, it's an internal variable used by MTA to identify the player who triggered the event.

Finally, do not forget to include the new gui.lua file in the meta.xml of the main resource, and label it as a client script:

``` xml
<script src="client/gui.lua" type="client" />
```

At this point, we now have a basic login window that checks the player's username and password when the login button is clicked. If they are correct, the player is automatically spawned.

For further help with GUI, see the [GUI tutorials](/docs/-category-gui_tutorials.md "wikilink").

[Category:GUI\_Tutorials](/docs/category-gui_tutorials.md "wikilink") [it:Introduzione\_allo\_scripting\_della\_GUI](/docs/it-introduzione_allo_scripting_della_gui.md "wikilink") [ru:Introduction to Scripting the GUI](/docs/ru-introduction_to_scripting_the_gui.md "wikilink") [es:Introducción a la Programación de GUI](/docs/es-introducción_a_la_programación_de_gui.md "wikilink")
