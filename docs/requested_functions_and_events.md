Server-side
-----------

Event like onServerTick wich is run very often. Like the clientside onClientRender. This could be useful for constat checking wich must be done under 50ms (lower than timers can handle).

------------------------------------------------------------------------

onVehicleCreated or an equivalent... shouldn't be too hard? -Robhol (14:15 Jul 6, 08)

  
If we did it, it'd be onElementCreated - what do you want this for? [eAi](/docs/user:eai.md "wikilink") 08:58, 7 July 2008 (CDT)

  
onElementCreated is a good idea - it could be used for lots of things. Also, how about onVehicleDrown or whatever? that is, when a vehicle hits deep water. Checking for collisions and stuff is very awkward, and client-side only, and has to be checked constantly.. -Robhol (17:31 Jul 9 08)

  
I second that. It would be useful if you use like me element data like the fuel amount or other stuff. And an event like this would help me to setup those element data, when a car spawns. Otherwise I would either have to edit every car spawn script I use or do a post-setup when someone is entering the car.. [User:MaddDogg14](/docs/user:madddogg14.md "wikilink") (04:34 Apr 4, 10 (CEST))

  
i definetly agree, onElementCreated would be VERY useful for utility/librares scripts, but i think this should be limited by ACL, because “evil” scripts could abuse this othervise -Karlis (9:10 Apr 5, 10)

------------------------------------------------------------------------

I ask for a function that detects if a ped is on floor, eg. **isPedOnFloor(ped thePed)**, thanks. --<span style="font-family:Courier New, Courier, monospace">[Shadd](/docs/user:shadd.md "wikilink")</span><sub>([In\\ caso\\ di\\ emergenza\\ rompere\\ le\\ scatole](/User_talk:Shadd.md "wikilink"))</sub> 11:29, 15 June 2008 (CDT)

  
[isPedOnGround](/docs/ispedonground.md "wikilink")? [Awwu](/User:Awwu.md "wikilink") 12:58, 15 June 2008 (CDT)

  
I need to know if the player has its back touching the ground, not if it's simply “on ground”. --<span style="font-family:Courier New, Courier, monospace">[Shadd](/docs/user:shadd.md "wikilink")</span><sub>([In\\ caso\\ di\\ emergenza\\ rompere\\ le\\ scatole](/User_talk:Shadd.md "wikilink"))</sub> 14:16, 16 June 2008 (CDT)

  
Check what task the player has, they should have TASK\_COMPLEX\_FALL\_AND\_GET\_UP or TASK\_COMPLEX\_FALL\_AND\_STAY\_DOWN... [eAi](/docs/user:eai.md "wikilink") 19:12, 16 June 2008 (CDT)

  
Thanks. What task does player have after being hitten by a melee attack that cause it to fall down? Would “TASK\_SIMPLE\_BE\_KICKED\_ON\_GROUND” and “TASK\_SIMPLE\_GET\_UP” work? --<span style="font-family:Courier New, Courier, monospace">[Shadd](/docs/user:shadd.md "wikilink")</span><sub>([In\\ caso\\ di\\ emergenza\\ rompere\\ le\\ scatole](/User_talk:Shadd.md "wikilink"))</sub> 09:35, 17 June 2008 (CDT)

  
Try it, I'm not entirely sure. You should be able to produce some code to show the player's current tasks very easily... [eAi](/docs/user:eai.md "wikilink") 19:20, 17 June 2008 (CDT)

  
My goal is to edit the standard damage of the attacks, in this case i have to know when player is on ground to cause higher damage. However it doesn't seem to work, when i hit the player it simply gets up without animation with no damage. --<span style="font-family:Courier New, Courier, monospace">[Shadd](/docs/user:shadd.md "wikilink")</span><sub>([In\\ caso\\ di\\ emergenza\\ rompere\\ le\\ scatole](/User_talk:Shadd.md "wikilink"))</sub> 19:10, 19 June 2008 (CDT)

------------------------------------------------------------------------

It may looks strange and useless (waste of time?) but I think that it could be a awesome feature. Having a web browser. Like: <http://www.youtube.com/watch?v=wT1UR6qEgdg> <http://princeofcode.com/awesomium.php>

  
definetly useles and waste of time, suporting xfire enought. -karlis

  
Really Karlis, who asked you bro. It could be very useful, actually. For example, creating dynamic billboards. Instead of changing the TXD, they could set up a browser object over the billboard. That way they can also set up a timer to change the image, etc. [JacobS](/docs/user:jacobs.md "wikilink") 20:08, 1 August 2010 (UTC)

------------------------------------------------------------------------

There could be something like createBrowser( float x, float y, float z, \[float rx, float ry, float rz, float width, float high, string url, bool locked\] ) locked parameter: false = navigation bar present, true = no navigation bar toggleBrowserFullsceenMode(browser theBrowser, bool tog, \[bool smooth\]) smooth parameter: If set to true the browser will smoothly move from his ingame position to the fullscreen position toggleBrowserBackground(browser theBrowser, bool tog) Set the browser background transparent.

------------------------------------------------------------------------

Security: Disable file downloads, disable popups (disable flash, javascript and any other protocols than http and https \[no mailto and stuff...\]?)

------------------------------------------------------------------------

Should be a Client and server function. --[Masterofquebec](/docs/user:masterofquebec.md "wikilink") 00:10, 15 October 2009 (UTC)

------------------------------------------------------------------------

Support of tooltips from CEGUI would be cool. I saw a property for that, but it didn't work for me. [User:MaddDogg14](/docs/user:madddogg14.md "wikilink") (04:36 Apr 4, 10 (CEST))

------------------------------------------------------------------------

I request a function that gets all clothes from a ped, just like getPedClothes but for all bodyparts. With this function it would be more ease to save clothes to database.

  
That's so easy to do yourself that it's barely worth adding. Just loop all the indexes 0-17 and save them to a table. [Awwu](/docs/user:awwu.md "wikilink") 19:26, 17 April 2010 (UTC)

------------------------------------------------------------------------

[setProjectileTarget](/docs/setprojectiletarget.md "wikilink") for setting a projectile to target a specific entity. I am trying to create a Battlefield Bad Company type of gamemode and in that game, you can plant a 'tracer'. Any rocket fired (if the tracer is on screen) will seek the tracer. [LeetWoovie](/User:LeetWoovie.md "wikilink") 05:01, 19 April 2010 (UTC)

------------------------------------------------------------------------

(marcol07, June the 25th, 2010) I would like to have some function to create light source as element or sth like createFire, for example createLight(x,y,z,xrot,yrot,zrot,f,r,g,b) where “f” is an angle of lightning. or it is possible with some model or function? It would be good to create for example fog lamps or classic street lamps

------------------------------------------------------------------------

moveElement available for markers, objects, pedestrians and players or maybe more if you can do. [Socialz](/docs/user:socialz.md "wikilink") 13:10, 1 January 2012 (CET)

Client-Side
-----------

Function "**isPlayerStunting**" for add options to events "*onClientPlayerStuntStart*" and "*onClientPlayerStuntFinish*" --[Dfigfjf](/docs/user:dfigfjf.md "wikilink") 18:52, 4 October 2015 (UTC)

------------------------------------------------------------------------

Event “onClientVehicleFire”, which would be triggered when a vehicle shoots.

  
See [OnVehicleWeaponFire](/docs/onvehicleweaponfire.md "wikilink") --[X86dev](/User:X86dev.md "wikilink") 12:11, 19 April 2013 (UTC)

------------------------------------------------------------------------

Adding possibility to toggle radio hud label by **showHudComponent** -karlis

------------------------------------------------------------------------

Pickup events clientside please, onClientPickupHit onClientPickupUse.

------------------------------------------------------------------------

Would it be possible to add a color arg to guiGridListSetItemText()? Im trying to get each item colored differently in one list. Thanks, ABEL

------------------------------------------------------------------------

I need a function which could get current target of hydra or a HS rocket launcher, like when someone press space and targets a element, to get what element is it for calculating distance from it. **getPlayerOccupiedVehicleTarget** or **getPlayerHSTarget**. Thanks in advance -Nidza a.k.a. CodeMaster 2:26 PM 19th June 2008.

------------------------------------------------------------------------

It'd be useful to have something to disable elements of the default hud (weapon display, health display, armor, radar, etcetera) so that you can create your own HUDs. Something like **setHudElement(element name, toggle)**.

[Lord Xalphox](/docs/user:lord_xalphox.md "wikilink") 19:32, 22 March 2009 (CET)

  
[showPlayerHudComponent](/docs/showplayerhudcomponent.md "wikilink")? [Awwu](/User:Awwu.md "wikilink") 19:43, 22 March 2009 (CET)

------------------------------------------------------------------------

I'd like to have a function that sets the chatbox input line text. Then I could script my own chat history function (that inserts the last sent text into the input line again by pressing arrow up) (which samp has since 0.2 btw) since nobody builds it into the client. [NeonBlack](/docs/user:neonblack.md "wikilink") 12:03, 4 July 2009 (CEST) PS.: samp also supports cut, copy and paste :P

------------------------------------------------------------------------

A function setElementMatrix, doing the exact opposite of getElementMatrix would be much appreciated. --[Kayl](/docs/user:kayl.md "wikilink") 15:21, 13 November 2009 (UTC)

------------------------------------------------------------------------

Functions like setTrainPosition(train,track,pos) and track,pos getTrainPosition(train) would be great in order to allow more script side control of trains. The track argument would be an index of the track number (currently there are around 4 tracks handled, including 1 incompletely defined). The position would be a float between 0 and 1 (or however you guys handle it) telling where on the track the train currently is. It would be great if those functions could be available client and server side. --[Kayl](/docs/user:kayl.md "wikilink") 12:58, 23 November 2009 (UTC)

------------------------------------------------------------------------

need this function client and server side **movePlayerHudComponent(string component, float x, float y)** --[SuatEyrice](/docs/user:suateyrice.md "wikilink") 00:18, 26 February 2010 (UTC)

------------------------------------------------------------------------

**(marcol07, June the 27th, 2010)** I would be so happy to have fuction to set Analog control of player sth like **getAnalogControlState(string controlName)** but inverted to **setAnalogControlState(string controlName, float state)**

------------------------------------------------------------------------

OnPedDamage (serverside) event. There is OnClientPedDamage, but it's clientside. [damage22](/docs/user:damage22.md "wikilink")

------------------------------------------------------------------------

**setRadioVolume(element thePlayer, int volume)**, to create GUI volume control, turn off the radio without changing the station, etc. [JacobS](/docs/user:jacobs.md "wikilink") 14:47, 29 July 2010 (UTC)

------------------------------------------------------------------------

**setVehicleHydraulics(element theVehicle, bool state)**, to force hydraulics to be up (true) or down (false)

------------------------------------------------------------------------

**createFire(x, y, z, theSize, dimension)**, just like [createFire](/docs/createfire.md "wikilink"), only with the option to enter a dimension for the fire to appear in

------------------------------------------------------------------------

**setGunshotsEnabled(bool enabled)**, **getGunshotsEnabled()** and **createGunshot(x,y,z,radius)** - to enable/disable the game's gunshot ambience, and to create gunshots at specific locations with radii that it is audible in [JacobS.](/docs/user:jacobs..md "wikilink") 19:28, 11 September 2010 (MDT)

------------------------------------------------------------------------

onClick should pass the name of the clicked SUBobject too (eg: vehicle parts, bone names etc.)--[Lcaseidefensis](/docs/user:lcaseidefensis.md "wikilink") 16:48, 21 May 2012 (UTC)

------------------------------------------------------------------------

something to open/close doors like in singleplayer (teleports are a bit unrealistic)

------------------------------------------------------------------------

moveCamera( player thePlayer, float positionX, float positionY, float positionZ \[, float lookAtX, float lookAtY, float lookAtZ, float roll = 0, float fov = 70 \] ) and attachElementToPed( player thePlayer, element theElement, interger bone)
