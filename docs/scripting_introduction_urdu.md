Ye Scripting Introduction Urdu Meu Originally Translate Ki Gai Hai, Is Meu Kisi Bhi Tarah Ke Translator Ki Madad Nahi Li Gai, Ye Officially Created Ki Gai Hi By [Bilal](/docs/user-bilal.md "wikilink"). Ye tutorial ab complete hai.

Lets Start
----------

Resources mta ka hissa hoti hain. Aik resource main collection of files hoti hain, plus aik meta file hoti hai jo describe karti hai ke kese resource ko load kiye jai aur ye resource kya contain karti hai. Resource ko start bhi kiya ja sakta hai aur stop bhi, aik waqt par aik se zyada bhi scripts chal sakti hain.

Scripting ka sab kuch resource mein hi hota ha. MTA resources ke saath aata hai jo ap apne game mode meu chahain to use kar sakte hain, jese ke map limits jo players ko aik makhsoos area meu play karne ko force karte hain, ya phir deathpickups resource jo player ki death par us ke weapons ko show karti hai.

Aik Working Script Ko Banana
----------------------------

Sab se pehle ham sekheu ge ke kese aik basic script ko banaya jaata hai jo players ko city ke around walk karne dete hain, Baari baari.

### Saari Scripts Kahan Par Hoti Hain?

Chaleu, ham script ke file structure ko dekhte hain. Apne MTA Server folder meu jain aur neeche path ko follow kareu:

`   server/mods/deathmatch/resources/`

Aap bohat sey zip files ko dekheu gay jo ke packaged simple scripts hain. Har file aik resource hai. Ye sab khud ba khud unzip ho kar load ho jain gi jese hi mta local server start ho ga. Aik script banane ke liye simply aik folder create kareu aur is meu jain. Ham “myserver” is tutorial ke liye use kareu gay. Ab ap ko is directory mein hona chahiye:

`   server/mods/deathmatch/resources/myserver/`

### Identify Resource Ko Karna

Taake server ko pata chale ke ye resource mein kya hai, aik *meta.xml* file ko create karna bohat zaroori hai. Ye file ko root directory mein hona chahiye, jo ke “myserver” hai hamare case meu. To ab aik text file create kareu aur isay name deu “meta.xml”, aur ise open kareu notepad se.

Phir ye walay codes *meta.xml* file meu enter kar deu:

``` xml
<meta>
     <info author="YourName" type="gamemode" name="My Server" description="My first MTA server" />
     <script src="script.lua" />
</meta>
```

Is *<info />* tag meu, aik field “type” bhi hai jo batata hai ke ye resource *gamemode* hai jab ke ''map' ya phir *script* nahi hai jo ke later explained kar diya jai ga. Gamemode aik cheez hai jis meu bohat saari scripts hoti hain. ''

<script />
'' tag batata hai ke is script meu konsi files hain, jo ke ham agge banaain gay.

### Aik Simple Script Ko Banana

Is baat ka khyaal rakheu ke ''

<script />
'' tag aik aur .lua file ke andar nahi hota, ye ussi directory mein hota hai jahan par meta.xml hota hai. Ab ap ye code ko copy aur paste kar sakte hain script.lua mein.

``` lua
local spawnX, spawnY, spawnZ = 1959.55, -1714.46, 10
function joinHandler()
    spawnPlayer(source, spawnX, spawnY, spawnZ)
    fadeCamera(source, true)
    setCameraTarget(source, source)
    outputChatBox("Welcome to My Server", source)
end
addEventHandler("onPlayerJoin", getRootElement(), joinHandler)
```

Ye script ap ko coordinate (x, y, z) pe saw kare gi, jab ap game ko join kareu gay. Is baat ka khyaal rahe ke *fadecamera* function zaroor hona chahiye warna ap ko sirf black screen hi dikhai de gi. Is ke saath saath ap camera target bhi set karna ho ga, warna saare players sirf sky ko hi dekh paain ge.

*source* variable batata hai ke kis ne event ko trigger kiya hai. Jab koi player join karta hai, ap is code ko ye pata lagane ke liye use kar sakte hain ke kis ne join kiya hai. So ye spawn hameu kisi random player pe nahi kare gi.

Agar ham gor se dekhey [addEventHandler](/docs/addeventhandler.md "wikilink") ko, to ap ko 3 cheezeu nazar aain gi, 'onPlayerJoin', jo batata hai jab event ko trigger kiya jaata hai. 'getRootElement()', jo batata hai ke kya/kis par ye trigger kiya jaa sakta hai. Aur 'joinHandler' jo batata hai ke konsa function trigger ho ga jab ham event ko trigger kareu gay. Aur details agge explain ki jain gi aik aur example main, ab ham server ko start karte hain aur script ko try karte hain!

### Script Ko Chalana

Server ko start karne ke liye, ap ko simply chalana hai excutable jo ke server directory main hai. Stats ki list sab se pehle show ho gi, is baat ka khyaal rakheu ke port number, ap ko game join karne ke liye chahiye ho ga. Phir server saari resources ko load kar leta hai aur phir “Ready to accept connections!” Connect karne se pehle, ap ko gamemode run karna bohat zaroori hai. Type kareu “start myserver” aur enter press kareu. Server gamemode ko start kar de ga jo ap ne abhi banaya, aur ab se koi errors aur warnings bhi show kare ga. Ab ap MTA ko start kareu, aur “Quick Connect” main apnay IP adress se connect kareu. Agar sab kuch theek hota hai, kuch der baad ap ka character streets pe walk kar raha ho ga Los Santos ki.

Ab aage ham command daleu gay jo players vehicle ko spawn karne ke liye use kar sakte hain apne position pe. Ap shaid is ko skip kar deu aur check kareu [Map Manager](/docs/map_manager.md "wikilink"), jo is tutorial ko continue karta hai. Is tutorial ki aik aur branch bhi hai, [Introduction to Scripting GUI](/docs/introduction_to_scripting_gui.md "wikilink"), ap is ko follow kar sakte hain aur pata chala sakte hain ke kese MTA Graphical User Interface MTA meu draw ki jaati hai aur kese script ki jaati hai.

Aik Simple Command Ko Banana
----------------------------

Chaleu ham dobarah *script.lua* content meu jaate hain. Jese ke ooper mention kiya, ham chahtay hain ke command par hamaray saath aik vehicle spawn go, sab se pehle hameu aik function banana ho ga, jis ko ham call kareu ge aur aik command handler jo command ko create karta hai.

``` lua
-- Function ko banain, jo command handler ko call karta hai in arguments sey: thePlayer, command, vehicleModel
function createVehicleForPlayer(thePlayer, command, vehicleModel)
   -- Vehicle ko banana aur doosri cheezeu.
end

-- Command handler ko banana.
addCommandHandler("createvehicle", createVehicleForPlayer)
```

*Note: Function names click able hote hain wiki par, in ko click kareu in ke baare meu information haasil karne ke liye*

#### Command Handlers Ke Baare Meu

Pehla argument command handler ke baare meu command ka name hai jo ke player ko enter karne ke liye allow kare gi. Doosra argument function hai jo ye call kare ga, is case meu *createVehicleForPlayer* Agar ap ka already scripting meu experience hai, ap ko is tarah ke function ke baare meu pata ho ga:

``` lua
functionName(argument1, argument2, argument3, ..)
```

``` lua
functionName(thePlayer, commandName, argument3, ..)
```

Agar ham gor se dekheu above example ko, ham dekh sakhte hain argument1 jo ke thePlayer hai aur argument2 commandName hai. thePlayer woh hai jis ne command ko type kiya ho ga. Isi liye ap jo bhi isay kaheu, variable contain kare ga player jis ne is command ko activate kiya ho ga. commandName woh hai jo player ne type ki ho gi. Agar woh type kareu "/greet", ye argument contain kare ga “greet”. Argument 3 aik extra line hai jo ham ne type ki hai. Ham is ke baare meu seekheu ge thora sa aage. Is ko naa bhooleu ke first 2 arguments, standard arguments hain, lekin ap is ko koi bhi name de sakte hain.

Ham ne call kiya [addCommandHandler](/docs/addcommandhandler.md "wikilink") ko is way mein aur jab se *createVeicleForPlayer* aik function hai, ye bhi us tareeqay se call kiya jaa sakta hai. Lekin ham us ke liye command handler use kar rahe hain, jo ke aik similar manner meu isse call karta hai. Aik example: Koi type karta hai “createvehicle 468” game meu, console meu Sanchez ko spawn karne ke liye, Command handler call karta hai createVehicleForPlayer function ko, jese **'if**' ham code ke is line ko script meu leu gay:

``` lua
createVehicleForPlayer(thePlayer,"createvehicle","468") -- thePlayer player element hai, woh jis ne ye command type ki.
```

Jese ke ham dekh sakte hain, ye bohat se parameters provide karta hai: woh player jis ne is command ko call ki, woh command jo us ne enter ki aur text us ke baad jo us ko dikha, is case meu “468” vehicle id hai Sanchez ki. Pehle 2 parameters sae hain all command handlers ke saath, jo ke aap read kar sakte hain [addEventHandler](/docs/addeventhandler.md "wikilink") page par. Is fact ke liye, aap ko at least 2 parameters ko define karna hota hai jo ap us ke baad use karte hain.

*Note: Aap ko command handler ko add karna hota hai, handler function ko define karne ke baad, warne ye isse find nahi kar paai ga.*

#### Function Ko Write Karna

Function ko fill karne ke liye, jo ham ne banaya, hameu sochna pare ga ke hameu kya karna hai:

-   Player ki position ka pata chalana hai, taake hameu pata ho ke ham ne vehicle ko kahan spawn karna hai (Ham chahtay hain ke vehicle player ke saath spawn ho)
-   Calucate position ko karna zaroori hai jahan par ham ne vehicle ko spawn karna hai. (Ham nahi chahtay ke vehicle player ke ooper spawn ho)
-   Vehicle ko spawn karna hai.
-   Check karna hai ke vehicle spawn hua hai ke nahi, aur aik message ko output karna hai.

Apne goals ko achieve karne ke liye, hameu bohat se functions use karne pareu gay. Functions ko find karne ke liye, hameu visit karna chahiye [Sserver Functions List](/docs/scripting_functions.md "wikilink") Sab se pehle hameu aik function chahiye player ki position ka pata lagaane ke liye. Jab se players elements hain, ham sab se pehle jump karte hain **Element functions** jahan par hameu pata chalta hai [getElementPosition](/docs/getelementposition.md "wikilink") function ke baate meu. Function name ko click karne ke baad, hameu function ki description pata chal jai gi. Wahan par ham syntax dekh sakte hain, ye kya return karti hai aur usually aik example. Syntax hameu batata hai ke kon se arguments ham kar sakte hain aur karne hain submit. [getElementPosition](/docs/getelementposition.md "wikilink") ke liye syntax ye hai:

``` lua
float, float, float getElementPosition ( element theElement )
```

Ye 3 *float* function name ke front meu jo hain, ye return type hain. Is case meu, is ka matlab ye hai ke ye function 3 floating point numbers ko return karta hai. (x, y aur z), ap un arguments ko dekh sakte hain jo ap ne submit karne hain. Is case meu sirf element jis ki position ap janana chahtay hain, woh hamari example meu player hai.

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    -- get the position and put x, y, z variables.
    -- (local ka matlab hai, variables jo only hote hain current scope main, is case meu, the function)
    local x,y,z = getElementPosition(thePlayer)
end
```

Aage ham ye pakka karna chahtay hain ke ye vehicle player ke ooper spawn na ho, is liye ham 5 units add kareu gay *x* variable meu, jo vehicle ko player kay east main spawn kare ga.

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    local x,y,z = getElementPosition(thePlayer) -- Player ki position ko pata chalanay key liye ye use hota hai.
    x = x + 5 -- 5 units ko add karna hai x meu.
end
```

Ab hameu aik aur function chahiye jis se aik vehicle spawn ho. Isi liye, aik baar phir ham search kareu gay [Server Functions List](/docs/scripting_functions.md "wikilink") Jab se ham vehicles kay baare meu baat kar rahe hain, **Vehicle functions** section meu, ham choose kareu gay [createVehicle](/docs/createvehicle.md "wikilink") ko. Is function kay syntax meu, hamaray paas sirf aik return type hai, jo ke zyada common hai. Hum ne ye bhi dekha ke kuch arguments \[ \] se close huay hain, matlab ye optional hain. Hamaray paas already woh saare arguments hain jo hameu [createVehicle](/docs/createvehicle.md "wikilink") ke liye chahiyain, hamaray function meu. Woh position jo ham ne abhi calculate ki *x, y, z* variables main, aur model id jo ham ne provice ki thi command ke through (“createvehicle 468”) aur ham function ko access kar sakte hain as *vehicleModel* variable.

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    local x,y,z = getElementPosition(thePlayer) -- get the position of the player
    x = x + 5 -- add 5 units to the x position
    -- create the vehicle and store the returned vehicle element in the ''createdVehicle'' variable
    local createdVehicle = createVehicle(tonumber(vehicleModel),x,y,z)
end
```

Of course ye code ko improve kiya jaa sakta hai bohat say ways mein, lekin ham aik check banana chahtay hain ke ye vehicle create hui thi ya nahi. Jese ke ham read kar sakte hain [createVehicle](/docs/createvehicle.md "wikilink") page par, **Returns** ke neeche, function return hota hai, *false*, jab ye vehicle ko create nahi kar paya tha. Hum *createVehicle* variable ki value ko check karte hain.

Ab hamare paas poori complete script hai:

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    local x,y,z = getElementPosition(thePlayer) -- get the position of the player
    x = x + 5 -- add 5 units to the x position
    local createdVehicle = createVehicle(tonumber(vehicleModel),x,y,z)
    -- check if the return value was ''false''
    if (createdVehicle == false) then
        -- if so, output a message to the chatbox, but only to this player.
        outputChatBox("Failed to create vehicle.",thePlayer)
    end
end
addCommandHandler("createvehicle", createVehicleForPlayer)
```

Jese ke ap ko pata hai, ham ne aik naya function introduce kiya hai [outputChatBox](/docs/outputchatbox.md "wikilink").Ap ab functions ke documentation pages ko khud dekh sakte hain.Zyada advanced scripting kay liye, check kareu [Map Manager](/docs/map_manager.md "wikilink").

Ap Ko Kya Pata Hona Chahiye
---------------------------

Ap ne pehle hi resources, command handlers aur functions ko find karne ke baare meu parha hai documentation kay first paragraph mein. Lekin abhi bohat kuch learn karna rahta hai. Ye section ap ko short overview de ga in cheezou kay baate meu, aur related links ko bhi add kiya jai ga.

### Clientside Aur Serverside Scripts

Shaid ap ne kabhi (server/cilent) kay baare meu suna ho mta sa wiki par. MTA ki kuch coding server sided karni parti hai aur kuch cilent sided. Jese ke aik GUI - Graphical User Interface, kuch cilent sided is liye hoti hain kyun ke woh cilent sided zyada behtar cilentsided kaam karti hain, ya phir server sided sahi tarha kaam nahi karti hain. Lekin zyada tar functions mta ke server sided hi kaam karte hain.

Zyada tar scripts jo ap banin gay jese ke gamemodes, maps, server sided hi hon gi, jese ke ham ne likhi thi first section mein. Agar kuch server side kaam nahi karta, to ap ko us ko cilent sided banana ho ga. Cilent Sided script kay liye aap ko ordinary script file create karni ho gi, jis ko ap name deu gay *cilent.lua* aur is ko meta meu bhi add kareu gey, is tarah:

``` xml
<script src="client.lua" type="client" />
```

*type* ko agar aap add nahi kareu gey to woh automatically server side ban jai ga, is liye a ko batana parhey ga ke ye cilent sided script hai meta.xml meu. Cilent sided script download ho jai gi player ke computer meu jab woh join kare ga server ko. Is ke baare meu parhein zyada idhar [Client side scripts](/docs/client_side_scripts.md "wikilink").

### Mushkil Resources Ke Baare Meu

Pechla section meu briefly explain kar diya hai ke cilent sided scripts ko kese add karte hain resource mein, lekin abhi bohat kuch possible hai. Jese ke ooper bataya, ham kisi bhi tarha ki resource bana sakte hain. Chaleu kuch theortical resources ko dekhte hain. *meta.xml* ko dekh kar hameu pata chalta hai ke ye resource kya kar sakti hai.

#### Pehle Example - Utility Script

``` xml
/admin_commands
    /meta.xml
    /commands.lua
    /client.lua
```

``` xml
<meta>
    <info author="Someguy" description="admin commands" />
    <script src="commands.lua" />
    <script src="client.lua" type="client" />
</meta>
```

-   *commands.lua* admin commands provide karti hai, jese ban karna player ko, mute karna ya kuch aur jo admins kar sakte hain.
-   *client.lua* aik gui provide karti hai jahan se ham actions ko perfom zyada asaani se kar paate hain.

Ye aik example hai jo har waqt run ho rahi hoti hai, aur ye bohat useful hai poorey game mode experience mein aur ye gameplay ke doraan interfere bhi nahi karti, jab tak koi admin action ko perform nahi karta.

#### Doosri Example - Aik Gamemode

``` xml
/counterstrike
    /meta.xml
    /counterstrike.lua
    /buymenu.lua
```

``` xml
<meta>
    <info author="Someguy" description="Counterstrike remake" type="gamemode" />
    <script src="counterstrike.lua" />
    <script src="buymenu.lua" type="client" />
</meta>
```

-   *counterstrike.lua* contain karta hai neeche diye gayi huay features:
    -   Players ko allow karti hai ke woh apni team ko choose kar paiin.
    -   Players ko weapons deti hai, targets aur instructions bhi deti hai.
    -   Game rules ko define karti hai, example ke tor par kab round end hota hai aur kya hota hai jab player mar jata hai.
    -   .. aur shaid more features.
-   *buymenu.lua* aik cilentside script hai jo aik menu ko create karti hai weapons ko buy karne ke liye.

Is example ko game mode kehte hain, jab se ye sirf gameplay se interfere nahi karti, balke rules ko define bhi karti hai. *type* batata hai ke ye example work kari hai [Map manager](/docs/map_manager.md "wikilink") kay saath. Is ka ye bhi matlab hai ke ye game mode map kay bagair nahi work karta. Gamemode ko hamesha generic hona chahiye. Next example meu aik map start hota hai.

#### Teesri Example - Aik Map

``` xml
/cs-airport
    /meta.xml
    /airport.map
    /airport.lua
```

``` xml
<meta>
    <info author="Someguy" description="Counterstrike airport map" type="map" gamemodes="counterstrike" />
    <map src="airport.map" />
    <script src="airport.lua" />
</meta>
```

-   *airport.map* XML file information provide karti hai map ke baare meu.
    -   Players ko kahan spawn hona chahiye, konse weapons meu hona chahiye.
    -   Targets konse hain.
    -   Weather, World Time, Timelimit
    -   Vehicles ko provide karna.
-   *airport.lua* shaid contain kareu map-specific cheezeu, jin meu shaid hon:
    -   Kuch cheez ka explode hona agar kuch specific hota hai.
    -   Custom objects ko banana ya move karna.
    -   Aur kuch jo ap soch sakte hain..

Jese ke ap dekh sakte hain ke *type* badal gaya hai 'map' meu, jo hameu bata raha hai ke [Map manager](/docs/map_manager.md "wikilink") resource aik map hai, jab ke *gamemodes* bata raha hai ke ye map valid hai, game mode is example ke ooper hai. Shaid ap ko ye kuch surprise lage kyun ke aik aur script bhi hai mao resource main. Ofcourse ye necessarily map meu nahi chahiye, lekin ye bohat se possibilities ko open kar deti hai map makers kay liye, ke woh apna world bana paiin. The *airport.map* file might look similiar to this:

``` xml
<map mode="deathmatch" version="1.0">
    <terrorists>
        <spawnpoint posX="2332.23" posY="-12232.33" posZ="4.42223" skins="23-40" />
    </terrorists>
    <counterterrorists>
        <spawnpoint posX="2334.23443" posY="-12300.233" posZ="10.2344" skins="40-50" />
    </counterterrorists>

    <bomb posX="23342.23" posY="" posZ="" />
    
    <vehicle posX="" posY="" posZ="" model="602" /> 
    <vehicle posX="" posY="" posZ="" model="603" /> 
</map>
```

Jab koi game mode start hota hai aik map ke saath, map resource khud ba khud start ho jati hai map manager ki waja se aur ye jo information contain karti hai, woh game mode read kar sakta hai. Jab koi map badalta hai, pehle wala map stop ho jata hai aur naya start ho jata hai, zyada explanation ke liye visit kareu [Writing Gamemodes](/docs/writing_gamemodes.md "wikilink") page ko.

### Events

Events kuch aise cheezeu hain jo mta ko batati hain un cheezou ke baare meu jo hoti hain. Jese ke jab koi player mar jata hai, [onPlayerWasted](/docs/onplayerwasted.md "wikilink") event ko trigger kiya jaata hai. Agar hameu koi action ko perforum karna hai jab koi player mar jaata hai, ap ko apne aap ko tyaar rakhna hai aik command handler ko dalne ke liye, jese ke is meu hai [Sab Se Pehla Chapter](/docs/#aik_working_script_ko_banana.md "wikilink").

Ye example aik message output kare gi us player ke naam se jo marra ho ga:

``` lua
function playerDied(totalAmmo, killer, killerWeapon, bodypart)
    outputChatBox(getPlayerName(source).." died!")
end
addEventHandler("onPlayerWasted",getRootElement(),playerDied)
```

Documentation page Events ka batata hai ke parameters pass kiye jaate hain handler function pe, Is se milta julta aik [Command Handlers](/docs/#command_handlers_ke_baare_meu.md "wikilink") har event aik doosre se different hota hai. Aik aur important point hai *source* variable, jo ke handler functions meu exist karta hai. Is ko parameter list meu add karne ki koi zaroorat nahi, lekin fir bhi ye exist karta hai. Player events ke liye, (Ooper Example), ye player element hai. Aik aur example ke liye, ap dekh sakte hain pehla section aik idea ke liye ke *source* kis tarha use hota hai.

Yahan Se Ab Kahan Jain?
-----------------------

Ab ap ko mta ki basic scripting ka pata chal chuka ho gaya ho ga aur thora sa documentation ke baare meu bhi. [Main Page](/docs/main_page.md "wikilink") zyada information ke baare meu links deta hai, tutorials jo ap ko allow karte hain ke ap zyada acha learn kar sakeu. {{note|Yahan se, ham recommend karte hain ke ap [debugging](/docs/debugging.md "wikilink") tutorial parheu. Ache debugging skills necessity hote hain jab ap scripts ko bana rahe hote hain. Ham ap ko [predefined variables list](/docs/predefined_variables_list.md "wikilink") ko parhne ki advice bhi dete hain, ye ap ko certain tasks meu help kare ga. **See also:**

-   [Advanced Topics](/docs/advanced_topics.md "wikilink")
-   [OOP English Scripting Introduction](/docs/oop_introduction.md "wikilink")

[es:Introducción a la Programación](/docs/es-introducción_a_la_programación.md "wikilink") [it:Introduzione allo scripting](/docs/it-introduzione_allo_scripting.md "wikilink") [nl:Scripting\_introductie](/docs/nl-scripting_introductie.md "wikilink") [pt-br:Introdução ao Scripting](/docs/pt-br-introdução_ao_scripting.md "wikilink") [ru:Scripting Introduction](/docs/ru-scripting_introduction.md "wikilink") [ar:مقدمه\_في\_البرمجه](/docs/ar-مقدمه_في_البرمجه.md "wikilink") [zh-cn:脚本编写介绍](/docs/zh-cn-脚本编写介绍.md "wikilink") [Category:Tutorials](/docs/category-tutorials.md "wikilink")
