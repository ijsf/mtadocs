This SDK allows you to call exported MTA functions from Java over HTTP.

Getting Started
---------------

To use it, you need to add library to your class-path. It's included in the zip file below.

To get started, copy modules/ml\_sockets into your modules folder.And load that. After that, copy resources/jsdk into your resources folder.And start that.

Classes
-------

### com.mtasa.elements.Resource

<code lang="java5"> public String getName(); public com.mtasa.MTA getServer(); public void setServer(com.mtasa.MTA newServer); public String getResourceInfo(String attr); public boolean setResourceInfo(String attr, String newVal); public boolean stopResource(); public boolean startResource(); public com.mtasa.LuaArgs call(String functionName,LuaArgs parameters); public String toString();

</syntaxhighlight>
### com.mtasa.elements.Element

<code lang="java5"> public String getType(); public boolean is\_a(Class&lt;?&gt; compareElement); public boolean clearElementVisibleTo(Element visibleTo); public Element cloneElement(); public boolean destroyElement(); public Point3D getElementPosition(); public boolean setElementPosition(double x,double y,double z); public boolean setElementPosition(Point3D points); public Point3D getElementRotation(); public boolean setElementRotation(double x,double y,double z); public boolean setElementRotation(Point3D points); public int getElementAlpha(); public boolean setElementAlpha(int alpha); public float getElementHealth(); public boolean setElementHealth(float health); public int getElementModel(); public boolean setElementModel(int model); public int getElementInterior(); public boolean setElementInterior(int interior); public int getElementDimension(); public boolean setElementDimension(int dimension); public Point3D getElementVelocity(); public boolean setElementVelocity(double x,double y,double z); public boolean setElementVelocity(Point3D points); public boolean isElementVisibleTo(Element element); public boolean setElementVisibleTo(Element element,boolean visible); public boolean isElementFrozen(); public boolean setElementFrozen(boolean frozen); public String getElementID(); public boolean setElementID(String new\_id); public String getElementData(String data\_name); public boolean setElementData(String data\_name,String newVal);

</syntaxhighlight>
### com.mtasa.elements.Ped extends Element

<code lang="java5"> All Element Functions; // Cloth Types public static final int CLOTH\_SHIRT = 0; public static final int CLOTH\_HEAD = 1; public static final int CLOTH\_TROUSERS = 2; public static final int CLOTH\_SHOES = 3; public static final int CLOTH\_TATTOOS\_LEFT\_UPPER\_ARM = 4; public static final int CLOTH\_TATTOOS\_LEFT\_LOWER\_ARM = 5; public static final int CLOTH\_TATTOOS\_RIGHT\_UPPER\_ARM = 6; public static final int CLOTH\_TATTOOS\_RIGHT\_LOWER\_ARM = 7; public static final int CLOTH\_TATTOOS\_BACK = 8; public static final int CLOTH\_TATTOOS\_LEFT\_CHEST = 9; public static final int CLOTH\_TATTOOS\_RIGHT\_CHEST = 10; public static final int CLOTH\_TATTOOS\_STOMACH = 11; public static final int CLOTH\_TATTOOS\_LOWER\_BACK = 12; public static final int CLOTH\_NECKLACE = 13; public static final int CLOTH\_WATCH = 14; public static final int CLOTH\_GLASSES = 15; public static final int CLOTH\_HAT = 16; public static final int CLOTH\_EXTRA = 17;

// Fighting Styles public static final int STYLE\_STANDARD = 4; public static final int STYLE\_BOXING = 5; public static final int STYLE\_KUNG\_FU = 6; public static final int STYLE\_KNEE\_HEAD = 7; public static final int STYLE\_GRAB\_KICK = 15; public static final int STYLE\_ELBOWS = 16;

// Ped stats public static final int PROGRESS\_MADE = 0; public static final int TOTAL\_PROGRESS = 1; public static final int LONGEST\_BASKETBALL = 2;

public static final int DIST\_FOOT = 3; public static final int DIST\_CAR = 4; public static final int DIST\_BIKE = 5; public static final int DIST\_BOAT = 6; public static final int DIST\_GOLF\_CART = 7; public static final int DIST\_HELICOPTOR = 8; public static final int DIST\_PLANE = 9; public static final int LONGEST\_WHEELIE\_DIST = 10; public static final int LONGEST\_STOPPIE\_DIST = 11; public static final int LONGEST\_2WHEEL\_DIST = 12;

public static final int WEAPON\_BUDGET = 13; public static final int FASHION\_BUDGET = 14; public static final int PROPERTY\_BUDGET = 15; public static final int SPRAYING\_BUDGET = 16;

public static final int LONGEST\_WHEELIE\_TIME = 17; public static final int LONGEST\_STOPPIE\_TIME = 18; public static final int LONGEST\_2WHEEL\_TIME = 19; public static final int FOOD\_BUDGET = 20;

public static final int FAT = 21; public static final int STAMINA = 22; public static final int BODY\_MUSCLE = 23; public static final int MAX\_HEALTH = 24; public static final int SEX\_APPEAL = 25;

public static final int DIST\_SWIMMING = 26; public static final int DIST\_CYCLE = 27; public static final int DIST\_TREADMILL = 28; public static final int DIST\_EXCERSISE\_BIKE = 29; public static final int TATTOO\_BUDGET = 30; public static final int HAIRDRESSING\_BUDGET = 31; public static final int PROSTITUTE\_BUDGET = 33;

public static final int MONEY\_SPENT\_GAMBLING = 35; public static final int MONEY\_MADE\_PIMPING = 36; public static final int MONEY\_WON\_GAMBLING = 37; public static final int BIGGEST\_GAMBLING\_WIN = 38; public static final int BIGGEST\_GAMBLING\_LOSS = 39; public static final int LARGEST\_BURGLARY\_SWAG = 40; public static final int MONEY\_MADE\_BURGLARY = 41; public static final int LONGEST\_TREADMILL\_TIME = 44; public static final int LONGEST\_EXCERSISE\_BIKE\_TIME = 45; public static final int HEAVIEST\_WEIGHT\_BENCH\_PRESS = 46; public static final int HEAVIEST\_WEIGHT\_DUMBELLS = 47; public static final int BEST\_TIME\_HOTRING = 48; public static final int BEST\_TIME\_BMX = 49; public static final int LONGEST\_CHASE\_TIME = 51; public static final int LAST\_CHASE\_TIME = 52; public static final int WAGE\_BILL = 53; public static final int STRIP\_CLUB\_BUDGET = 54; public static final int CAR\_MOD\_BUDGET = 55; public static final int TIME\_SPENT\_SHOPPING = 56; public static final int TOTAL\_SHOPPING\_BUDGET = 62; public static final int TIME\_SPENT\_UNDERWATER = 63;

public static final int RESPECT\_TOTAL = 64; public static final int RESPECT\_GIRLFRIEND = 65; public static final int RESPECT\_CLOTHES = 66; public static final int RESPECT\_FITNESS = 67; public static final int RESPECT = 68;

public static final int WEAPONTYPE\_PISTOL\_SKILL = 69; public static final int WEAPONTYPE\_PISTOL\_SILENCED\_SKILL = 70; public static final int WEAPONTYPE\_DESERT\_EAGLE\_SKILL = 71; public static final int WEAPONTYPE\_SHOTGUN\_SKILL = 72; public static final int WEAPONTYPE\_SAWNOFF\_SHOTGUN\_SKILL = 73; public static final int WEAPONTYPE\_SPAS12\_SHOTGUN\_SKILL = 74; public static final int WEAPONTYPE\_MICRO\_UZI\_SKILL = 75; public static final int WEAPONTYPE\_MP5\_SKILL = 76; public static final int WEAPONTYPE\_AK47\_SKILL = 77; public static final int WEAPONTYPE\_M4\_SKILL = 78; public static final int WEAPONTYPE\_SNIPERRIFLE\_SKILL = 79; public static final int SEX\_APPEAL\_CLOTHES = 80; public static final int GAMBLING = 81;

public static final int PEOPLE\_KILLED\_BY\_OTHERS = 120; public static final int PEOPLE\_KILLED\_BY\_PLAYER = 121; public static final int CARS\_DESTROYED = 122; public static final int BOATS\_DESTROYED = 123; public static final int HELICOPTORS\_DESTROYED = 124; public static final int PROPERTY\_DESTROYED = 125; public static final int ROUNDS\_FIRED = 126; public static final int EXPLOSIVES\_USED = 127; public static final int BULLETS\_HIT = 128; public static final int TYRES\_POPPED = 129; public static final int HEADS\_POPPED = 130; public static final int WANTED\_STARS\_ATTAINED = 131; public static final int WANTED\_STARS\_EVADED = 132; public static final int TIMES\_ARRESTED = 133; public static final int DAYS\_PASSED = 134; public static final int TIMES\_DIED = 135; public static final int TIMES\_SAVED = 136; public static final int TIMES\_CHEATED = 137; public static final int SPRAYINGS = 138; public static final int MAX\_JUMP\_DISTANCE = 139; public static final int MAX\_JUMP\_HEIGHT = 140; public static final int MAX\_JUMP\_FLIPS = 141; public static final int MAX\_JUMP\_SPINS = 142; public static final int BEST\_STUNT = 143; public static final int UNIQUE\_JUMPS\_FOUND = 144; public static final int UNIQUE\_JUMPS\_DONE = 145; public static final int MISSIONS\_ATTEMPTED = 146; public static final int MISSIONS\_PASSED = 147; public static final int TOTAL\_MISSIONS = 148; public static final int TAXI\_MONEY\_MADE = 149; public static final int PASSENGERS\_DELIVERED\_IN\_TAXI = 150; public static final int LIVES\_SAVED = 151; public static final int CRIMINALS\_CAUGHT = 152; public static final int FIRES\_EXTINGUISHED = 153; public static final int PIZZAS\_DELIVERED = 154; public static final int ASSASSINATIONS = 155; public static final int LATEST\_DANCE\_SCORE = 156; public static final int VIGILANTE\_LEVEL = 157; public static final int AMBULANCE\_LEVEL = 158; public static final int FIREFIGHTER\_LEVEL = 159; public static final int DRIVING\_SKILL = 160; public static final int TRUCK\_MISSIONS\_PASSED = 161; public static final int TRUCK\_MONEY\_MADE = 162; public static final int RECRUITED\_GANG\_MEMBERS\_KILLED = 163; public static final int ARMOUR = 164; public static final int ENERGY = 165; public static final int PHOTOS\_TAKEN = 166; public static final int KILL\_FRENZIES\_ATTEMPTED = 167; public static final int KILL\_FRENZIES\_PASSED = 168; public static final int FLIGHT\_TIME = 169; public static final int TIMES\_DROWNED = 170; public static final int NUM\_GIRLS\_PIMPED = 171; public static final int BEST\_POSITION\_HOTRING = 172; public static final int FLIGHT\_TIME\_JETPACK = 173; public static final int SHOOTING\_RANGE\_SCORE = 174; public static final int VALET\_CARS\_PARKED = 175; public static final int KILLS\_SINCE\_LAST\_CHECKPOINT = 176; public static final int TOTAL\_LEGITIMATE\_KILLS = 177; public static final int BLOODRING\_KILLS = 178; public static final int BLOODRING\_TIME = 179; public static final int NO\_MORE\_HURRICANES = 180; public static final int CITIES\_PASSED = 181; public static final int POLICE\_BRIBES = 182; public static final int CARS\_STOLEN = 183; public static final int CURRENT\_GIRLFRIENDS = 184; public static final int BAD\_DATES = 185; public static final int GIRLS\_DATED = 186; public static final int TIMES\_SCORED\_WITH\_GIRL = 187; public static final int DATES = 188; public static final int GIRLS\_DUMPED = 189; public static final int TIMES\_VISITED\_PROSTITUTE = 190; public static final int HOUSES\_BURGLED = 191; public static final int SAFES\_CRACKED = 192; public static final int STOLEN\_ITEMS\_SOLD = 194; public static final int EIGHT\_BALLS\_IN\_POOL = 195; public static final int WINS\_IN\_POOL = 196; public static final int LOSSES\_IN\_POOL = 197; public static final int VISITS\_TO\_GYM = 198; public static final int MEALS\_EATEN = 200; public static final int UNDERWATER\_STAMINA = 225; public static final int BIKE\_SKILL = 229; public static final int CYCLE\_SKILL = 230; // Functions: public boolean addPedClothes(String texture,String model, int type); public boolean doesPedHaveJetPack(); public String\[\] getPedClothes(int clothesType); public int getPedFightingStyle(); public boolean setPedFightingStyle(int style); public float getPedGravity(); public boolean setPedGravity(float style); public int getPedSkin(); public boolean setPedSkin(int skin); public float getPedRotation(); public boolean setPedRotation(float rot); public boolean givePedJetpack(); public boolean removePedJetpack(); public Vehicle getPedOccupiedVehicle(); public float getPedStat(int stat);

</syntaxhighlight>
### com.mtasa.elements.Player extends Ped

<code lang="java5"> All Element Functions; All Ped Functions; public String getPlayerName(); public String getPlayerName(boolean removecolorcodes); public String getPlayerIP(); public String getPlayerSerial(); public int getPlayerMoney(); public int getPlayerPing(); public Team getPlayerTeam(); public int getPlayerWantedLevel(); public boolean givePlayerMoney(int money); public boolean isPlayerMuted(); public boolean setPlayerMoney(int money); public boolean setPlayerMuted(boolean muted); public boolean setPlayerTeam(Team team); public boolean spawnPlayer(double x,double y,double z); public boolean spawnPlayer(Point3D p); public boolean spawnPlayer(Point3D point,double rot,int skin,int interior,int dimension,Team team);

</syntaxhighlight>
### com.mtasa.elements.Blip extends Element

<code lang="java5"> All Element Functions; // Functions will be added soon..

</syntaxhighlight>
### com.mtasa.elements.CollisionShape extends Element

<code lang="java5"> All Element Functions; // Functions will be added soon..

</syntaxhighlight>
### com.mtasa.elements.GTAObject extends Element

<code lang="java5"> All Element Functions; // Functions will be added soon..

</syntaxhighlight>
### com.mtasa.elements.Pickup extends Element

<code lang="java5"> All Element Functions; // Functions will be added soon..

</syntaxhighlight>
### com.mtasa.elements.RadarArea extends Element

<code lang="java5"> All Element Functions; // Functions will be added soon..

</syntaxhighlight>
### com.mtasa.elements.Team extends Element

<code lang="java5"> All Element Functions; // Functions will be added soon..

</syntaxhighlight>
### com.mtasa.elements.Vehicle extends Element

<code lang="java5"> All Element Functions; // Functions will be added soon..

</syntaxhighlight>
### com.mtasa.functions.ElementFuncs

<code lang="java5"> public MTA getServer(); public void setServer(MTA server); public static String type\_to\_string(Class&lt;? extends Element&gt; type); public <E extends Element> E\[\] getElementsByType(Class<E> type); public Object\[\] getElementsByType(String type); public Element createElement(String type); public Element getElementByID(String id);

</syntaxhighlight>
### com.mtasa.functions.Output

<code lang="java5"> public static final int LEVEL\_CUSTOM = 0; public static final int LEVEL\_ERROR = 1; public static final int LEVEL\_WARNING = 2; public static final int LEVEL\_INFO = 3;

// Functions:

public MTA getServer(); public void setServer(MTA server); public boolean outputChatBox(Object message); public boolean outputChatBox(Object message,Element toElement); public boolean outputChatBox(Object message,Element toElement,int r,int g,int b); public boolean outputChatBox(Object message,Element toElement,int r,int g,int b,boolean colorcoded); public boolean outputConsole(Object message); public boolean outputConsole(Object message,Element toElement); public boolean outputDebugString(Object message); public boolean outputDebugString(Object message,int dlevel); public boolean outputDebugString(Object message,int dlevel,int r,int g,int b); public boolean outputServerLog(Object message);

</syntaxhighlight>
### com.mtasa.functions.PlayerFuncs

<code lang="java5"> public MTA getServer(); public void setServer(MTA server); public Player getPlayerFromName(String name); public Player getPlayerFromNamePart(String name); public Player\[\] getAlivePlayers(); public Player\[\] getDeadPlayers(); public Player getRandomPlayer(); public int getPlayerCount()

</syntaxhighlight>
com.mtasa.LuaArgs extends java.util.List
----------------------------------------

<code lang="java5"> All list functions.So, you can use in generic for. public MTA getServer(); public void setServer(MTA server); public Element parseElement(int index); public Player parsePlayer(int index); public Pickup parsePickup(int index); public Ped parsePed(int index); public Blip parseBlip(int index); public CollisionShape parseCollisionShape(int index); public GTAObject parseGTAObject(int index); public RadarArea parseRadarArea(int index); public Team parseTeam(int index); public Vehicle parseVehicle(int index) ; public Resource parseResource(int index) ; public String parseString(int index); public Boolean parseBoolean(int index); public Double parseDouble(int index); public Float parseFloat(int index); public Integer parseInt (int index); public String toJson(); public void loadFromJSON(String json); public Object\[\] jsonToObject(String json); public static String toJson(Object o); public static Object\[\] fromJson(String j); public Object get(int index);

</syntaxhighlight>
com.mtasa.MTA
-------------

<code lang="java5"> public Output out; public Element rootElement; public PlayerFuncs players; public ElementFuncs elements; public static final String RESOURCE = “jsdk”; // JavaSDK Resource Name.

// Functions; public void sockOpen(); // Port will used in callJava (Changed) public Element parseElement(Object o); public Resource parseResource(Object o); public void sockClose(); public int getSocketPort(); public LuaArgs call(String resource,String function,LuaArgs args); // Function must be exported and given http=“true” public LuaArgs callFunction(String function,LuaArgs args); // This is for calling server-side functions.(etc:getElementByType) public LuaArgs luaArg(Object i); // This is for only 1 parameter arguments. // callJava Functions; public void addInputEvent(InputEvent e); // Only usable with callJava and sockOpen public void removeInputEvent(InputEvent e); // Only usable with callJava and sockOpen public void clearInputEvent(); // Only usable with callJava and sockOpen public ArrayList<InputEvent> getInputEvents(InputEvent e); // Only usable with callJava and sockOpen

// Getter-Setter; public void setHost(String host); public String getHost(); public void setPort(int port); public int getPort(); public void setUsername(String username); public String getUsername(); public void setPassword(String password); public String getPassword(); public String getCharset(); public void setCharset(String charset);

</syntaxhighlight>
com.mtasa.InputEvent( Interface )
---------------------------------

<code lang="java5"> public void onAction(LuaArgs args, String input) throws MTAException

</syntaxhighlight>
com.mtasa.MTAException extends Exception
----------------------------------------

<code lang="java5"> All exception functions;

</syntaxhighlight>
Examples
--------

<code lang="java"> MTA server = new MTA(“localhost”,22005,“admin”,“12345”); // Sweet, we are creating a new instance and connection.

</syntaxhighlight>
<code lang="java"> /\* Example 1: \*/ Player\[\] players = server.elements.getElementsByType(Player.class); // ElementFuncs deployed in server.elements :) server.out.outputChatBox(“There are”+players.length+" players",server.rootElement,180,25,25,false); // You don't need getRootElement(), it's deployed in server.rootElement variable. LuaArgs ret = server.call(“rcon”,“getThisResource”,null); // We are calling getThisResource in rcon bot.It's exported :) Resource thisRes = ret.parseResource(0); // Now, we parsed argument to Resource object. Player playerRancho = server.players.getPlayerFromName(“Rancho”); // We're getting player named Rancho, if he has a colorcode. We must add this if (playerRancho != null){ // If playerRancho exists

`   server.out.outputChatBox("`<PM>` JavaSDK: #0055FFHello Sweety",playerRancho,255,255,255,true);`

}else{ // else

`   server.out.outputDebugString(`“`There` `is` `no` `named` `player` `RANCHO!`”`);`

}

</syntaxhighlight>
<code lang="java"> /\* Example 2 : \*/ Ped\[\] peds = server.elements.getElementsByType(Ped.class); // We deployed Peds in the peds variable. for (Ped ped: peds){ // Generic for, (foreach)

`   if (ped.doesPedHaveJetPack()) // If ped has a jetpack`
`       ped.removePedJetpack(); // remove him jetpack`
`   else // else`
`       ped.givePedJetpack(); // give him jetpack `

}

</syntaxhighlight>
<code lang="java"> /\* Example 3: \*/ Element\[\] myElements = server.elements.getElementsByType(“myElement”); // Now we get elements by the string type // To do :)

</syntaxhighlight>
<code lang="java"> /\* Example 4: for callJava \*/ server.sockOpen(); // callJava open ports server.addInputEvent(new InputEvent(){

`   @Override`
`   public void onAction(LuaArgs args, String input) throws MTAException{`
`       String event = args.parseString(0); // Argumant 1 :) It's not default argument :)`
`       if (event.equals(`“`onMyCall`”`)){`
`           System.out.println(`“`onMyCall:`”`+args.parseString(1));`
`       }`
`   }`

}); // lua file: for k,v in ipairs(exports.jsdk:getConnections()) do

`   exports.jsdk:callJava(v,`“`onMyCall`”`,`“`Hello`”`);`

end

</syntaxhighlight>
<code lang="java"> /\* Example 5: is\_a \*/ Player playerRancho = server.players.getPlayerFromName(“Rancho”); // We're getting player named Rancho, if he has a colorcode. We must add this

if (playerRancho != null){ // If playerRancho exists

`   LuaArgs myCallbackargs = new LuaArgs(server); // create new instance`
`   myCallbackargs.add(playerRancho); // add a new argument`
`   myCallbackargs.add(`“`How` `are` `u?`”`); // add a new argument`
`   LuaArgs ret = server.call(`“`rcon`”`,`“`returnElement`”`,myCallbackargs); // call the howAre function into rcon resource, and send the 2 parameter :) myCallbackargs`
`   for (Object o: ret){ // generic for returns`
`       Element e = (Element)o;`
`       server.out.outputServerLog(`“`Returned` `value` `is` `a` `player?:`”`+o.is_a(Player.class));`
`   }`

}else{ // else

`   server.out.outputDebugString(`“`There` `is` `no` `named` `player` `RANCHO!`”`);`

}

</syntaxhighlight>
-   [For more examples / tutorials](http://forum.mtasa.com/viewtopic.php?f=148&t=46367)

More complex example
--------------------

[Image:ExamplaSDK.png](/docs/Image:ExamplaSDK.png.md "wikilink")

Caveats
-------

-   You cannot currently compare two Resource or Element objects that you expect to be identical - you need to do a “deep compare”, comparing either the “id” fields or the “name” fields.
-   The zip contains src, and javadoc

Download
--------

-   [Download Version 0.2](https://rapidshare.com/files/3674532513/JavaSDK.zip)
-   [Download Version 0.1](http://www.solidfiles.com/d/7713c8510b/)

Contact
-------

If you have any questions/suggestions you can contact author on MTA forum.

-   [Skyline (laserlaser)](http://forum.mtasa.com/memberlist.php?mode=viewprofile&u=51246)

[Category:Scripting Concepts](/docs/Category:Scripting_Concepts.md "wikilink")
