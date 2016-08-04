<lowercasetitle/>

This useful shared function converts some text to audible speech using Google's TTS.

Syntax
------

``` Lua
 )
```

Required arguments
------------------

-   *text*: the text to convert to speech.

Optional arguments
------------------

-   *broadcastTo*: if it's a regular indexed table, the speech will be broadcasted to the players contained in it. If it's a element, the speech will be heard by the players which are children of that element. This parameter is **ONLY** serverside; if you're using this function clientside this will be considered as the *language* argument.
-   *language*: defines the language of the TTS output.

Returns
-------

-   This function returns *[nil](/nil.md "wikilink")* and outputs an error if an argument it's not valid.
-   If called serverside and if all arguments are valid, this function returns *true* if the client was successully told to play the TTS (althrough this doesn't mean that the client will always play the speech); *false* otherwise.
-   If called clientside and if all arguments are valid, this function returns *true*, the corresponding [sound](/sound.md "wikilink") element and its URL if the sound could theorically be played (althrough it may not play); *[nil](/nil.md "wikilink")* otherwise.

Function source
---------------

<section name="Client" class="client" show="true">
    addEvent("playTTS", true) -- Add the event

    local function playTTS(text, lang)
        local URL = "http://translate.google.com/translate_tts?tl=" .. lang .. "&q=" .. text
        -- Play the TTS. BASS returns the sound element even if it can not be played.
        return true, playSound(URL), URL
    end
    addEventHandler("playTTS", root, playTTS)

</section>
<section name="Shared (server and client)" class="both" show="true">
``` lua
function convertTextToSpeech(text, broadcastTo, lang)
    -- Ensure first argument is valid
    assert(type(text) == "string", "Bad argument 1 @ convertTextToSpeech [ string expected, got " .. type(text) .. "]")
    assert(#text <= 100, "Bad argument 1 @ convertTextToSpeech [ too long string; 100 characters maximum ]")
    if triggerClientEvent then -- Is this function called serverside?
        -- Ensure second and third arguments are valid
        assert(broadcastTo == nil or type(broadcastTo) == "table" or isElement(broadcastTo), "Bad argument 2 @ convertTextToSpeech [ table/element expected, got " .. type(broadcastTo) .. "]")
        assert(lang == nil or type(lang) == "string", "Bad argument 3 @ convertTextToSpeech [ string expected, got " .. type(lang) .. "]")
        -- Tell the client to play the speech
        return triggerClientEvent(broadcastTo or root, "playTTS", root, text, lang or "en")
    else -- This function is executed clientside
        local lang = broadcastTo
        -- Ensure second argument is valid
        assert(lang == nil or type(lang) == "string", "Bad argument 2 @ convertTextToSpeech [ string expected, got " .. type(lang) .. "]")
        return playTTS(text, lang or "en")
    end
end
```

</section>
-   Original author: *Has\[S\]oN*.
-   Skype: *hassan.saad2000*

Example
-------

This example disables text chat and converts that text to a speech audible to nearby players. **NOTE**: this example requires 1.4 in order to work.

<section name="Server" class="server" show="true">
    local function tellClientsToPlayTTS(text, type)
        if type == 0 and #text <= 100 then -- We only want to replace normal chat if possible
            local x, y, z = getElementPosition(source)
            local col = createColSphere(x, y, z, 30) -- We need this to get nearby players
            triggerClientEvent(getElementsWithinColShape(col, "player"), "playChatTTS", source, text) -- Tell the nearby clients to play the sound
            destroyElement(col)
            cancelEvent() -- Replace text chat
        end
    end
    addEventHandler("onPlayerChat", root, tellClientsToPlayTTS)

</section>
<section name="Client" class="client" show="true">
    addEvent("playChatTTS", true) -- Add the event

    local function playChatTTS(text)
        local lang = (getLocalization().code):sub(1, 2) -- Output the TTS in the local player language, but don't bother about variants
        local _, speech, URL = convertTextToSpeech(text, lang)
        -- Convert that speech to a 3D sound
        destroyElement(speech)
        local x, y, z = getElementPosition(source)
        local speech = playSound3D(URL, x, y, z)
        attachElements(speech, source) -- Make the sound follow the player
        setElementDimension(speech, getElementDimension(source))
        setSoundMinDistance(speech, 15)
        setSoundMaxDistance(speech, 30)
        -- Tricky thing ahead: make the player mouth move, but without rendering him unable to move
        setPedAnimation(source, "ped", "factalk", 0, true)
        setPedAnimation(source, "ped", "factalk", 0, true)
        -- Reset the player mouth after the speech has ended
        setTimer(function(player)
            if isElement(player) then
                setPedAnimation(player) -- Clear the animation
            end
        end, math.max(getSoundLength(speech) * 1000, 50), 1, source)
    end
    addEventHandler("playChatTTS", root, playChatTTS)

</section>
See also
--------
