This file is used to set your UI e.g. chat box color, chat font or even bind keys. You can modify it to make your chat box look better or add favourite servers manually. Coreconfig.xml is located in your MTA San Andreas 1.x\\MTA\\ folder with another file called [Chatboxpresents.xml](/docs/Chatboxpresents.xml.md "wikilink").

Settings
--------

Most of the settings are self-explained.

-   **nick** - Your nickname in-game
-   **host** - Last played server's IP
-   **port** - Last played server's port
-   **password** - Last played server's password
-   **qc\_host** - Quick Connect IP
-   **qc\_port** - Quick Connect Port
-   **qc\_password** - Quick Connect Password
-   **debugfile** -
-   **console\_pos** - X, Y co-ords of the screen where console should be shown (after pressing \` (tilde) key)
-   **console\_size** - The size of the console after setting it's co-ordinates.
-   **serverbrowser\_size** - The size of the server browser.
-   **fps\_limit** - The limit for your FPS(Frames Per Second)
-   **chat\_font** - Font ID you want to be used in chat box
-   **chat\_lines** - How many lines you want to be displayed in chat box
-   **chat\_color** - Chat box background color (format is: RGBA, values between 0 - 255)
-   **chat\_input\_color** - Background of the line shown when you type text (displayed when you press T or Y)
-   **chat\_input\_prefix\_color** - Color of the word “Say:” or “Team Say:” when you press T or Y
-   **chat\_input\_text\_color** - Color of the text you type, when you press T or Y
-   **chat\_scale** - Scale of the chat box, that is size of it (format is: width height, floating values between 0 - 1)
-   **chat\_width** - Width of the chat box, text will wrap if it reaches this end
-   **chat\_css\_style\_text** - (needs explanation)
-   **chat\_css\_style\_background** - (needs explanation)
-   **chat\_line\_life** - (needs explanation)
-   **chat\_line\_fade\_out** - Time after which line should fade out (milliseconds)
-   **chat\_use\_cegui** - Should chat use CEGUI? (values 0 or 1).
-   **text\_scale** - Scale of the text.
-   **invert\_mouse** - Should the mouse be inverted? (Values 0 or 1).
-   **fly\_with\_mouse** - Should you fly with mouse? (Values 0 or 1).
-   **steer\_with\_mouse** - Should you steer with the mouse? (Values 0 or 1).
-   **classic\_controls** - Should the classic controls be on? (Values 0 or 1).
-   **mtavolume** - Your MTA's Volume.
-   **voicevolume** - The in-game players voice volume.
-   **async\_loading** - (Explaination)
-   **menu\_options** - Contains the flags for the animated 3D menu scene (as given in the Video tab). Set to 255 to enable all options. Set to 248 to disable all options in case of problems/issues in the main menu (and not during game play).

Bind key
--------

Binding key format is easy and almost everyone can bind their own keys to make the game easier to play and speed up your gaming a little bit. You can bind a command you use the most often to a key, so when you press the key that command will execute.

Example binding key “h” which will execute /help command:

    <bind key="h" command="help" />

it's that simple. You can also use arguments in commands e.g. some servers have banking systems so you can /deposit money using keys too, eg:

    <bind key="[" command="deposit" arguments="1000" />

This will deposit your $1000.

Coreconfig.xml Files:
---------------------

<section name="1.4" class="client">
{{\#tag:code | <mainconfig>

`   `<settings>
`       `<nick></nick>
`       `<host>`128.0.0.1`</host>
`       `<port>`22003`</port>
`       `<password></password>
`       `<qc_host>`192.168.1.101`</qc_host>
`       `<qc_port>`22003`</qc_port>
`       `<qc_password></qc_password>
`       `<debugfile></debugfile>
`       `<console_pos>`59 328`</console_pos>
`       `<console_size>`689 450`</console_size>
`       `<serverbrowser_size>`720 495`</serverbrowser_size>
`       `<fps_limit>`100`</fps_limit>
`       `<chat_font>`1`</chat_font>
`       `<chat_lines>`10`</chat_lines>
`       `<chat_color>`0 0 0 0`</chat_color>
`       `<chat_input_color>`0 0 0 0`</chat_input_color>
`       `<chat_input_prefix_color>`172 213 254 255`</chat_input_prefix_color>
`       `<chat_input_text_color>`172 213 254 255`</chat_input_text_color>
`       `<chat_scale>`1 1`</chat_scale>
`       `<chat_width>`1.500000`</chat_width>
`       `<chat_css_style_text>`0`</chat_css_style_text>
`       `<chat_css_style_background>`0`</chat_css_style_background>
`       `<chat_line_life>`12000`</chat_line_life>
`       `<chat_line_fade_out>`3000`</chat_line_fade_out>
`       `<chat_use_cegui>`0`</chat_use_cegui>
`       `<text_scale>`1.000000`</text_scale>
`       `<invert_mouse>`0`</invert_mouse>
`       `<fly_with_mouse>`0`</fly_with_mouse>
`       `<steer_with_mouse>`0`</steer_with_mouse>
`       `<classic_controls>`1`</classic_controls>
`       `<mtavolume>`0.500000`</mtavolume>
`       `<voicevolume>`0.500000`</voicevolume>
`       `<async_loading>`1`</async_loading>
`       `<mapalpha>`127`</mapalpha>
`       `<browser_speed>`1`</browser_speed>
`       `<single_download>`0`</single_download>
`       `<code_path>`0`</code_path>
`       `<update_build_type>`0`</update_build_type>
`       `<volumetric_shadows>`0`</volumetric_shadows>
`       `<aspect_ratio>`0`</aspect_ratio>
`       `<display_windowed>`0`</display_windowed>
`       `<multimon_fullscreen_minimize>`0`</multimon_fullscreen_minimize>
`       `<screenshot_path>`C:\Program Files\MTA San Andreas 1.4\screenshots`</screenshot_path>
`       `<current_skin>`Default`</current_skin>
`       `<chat_text_color>`152 15 152 212`</chat_text_color>
`       `<fixup_flags>`-cb-ma`</fixup_flags>
`       `<community_username></community_username>
`       `<community_password></community_password>
`       `<save_server_passwords>`1`</save_server_passwords>
`       `<auto_refresh_browser>`1`</auto_refresh_browser>
`       `<streaming_memory>`247`</streaming_memory>
`       `<force_browse_other_versions></force_browse_other_versions>
`       `<reportsettings>`filter2@+all,-{1000~2007},-2050,-2051,-{3120},-{3211},-{4002},-5132,-5133,-5809,-7011,-7106,-7801,-7043,-7050,-7051,-7420,-7601,-{7842~7845},-7940;max@4001;min@11`</reportsettings>
`       `<anisotropic>`0`</anisotropic>
`       `<grass>`0`</grass>
`       `<network_encryption>`1`</network_encryption>
`       `<fast_clothes_loading>`1`</fast_clothes_loading>
`       `<allow_screen_upload>`1`</allow_screen_upload>
`       `<max_clientscript_log_kb>`5000`</max_clientscript_log_kb>
`   `</settings>
`   `<binds>
`       `<bind key="num_0" control="fire"></bind>
`       `<bind key="lctrl" control="fire"></bind>
`       `<bind key="mouse1" control="fire"></bind>
`       `<bind key="e" control="next_weapon"></bind>
`       `<bind key="num_enter" control="next_weapon"></bind>
`       `<bind key="q" control="previous_weapon"></bind>
`       `<bind key="num_dec" control="previous_weapon"></bind>
`       `<bind key="arrow_u" control="forwards"></bind>
`       `<bind key="w" control="forwards"></bind>
`       `<bind key="arrow_d" control="backwards"></bind>
`       `<bind key="s" control="backwards"></bind>
`       `<bind key="arrow_l" control="left"></bind>
`       `<bind key="a" control="left"></bind>
`       `<bind key="arrow_r" control="right"></bind>
`       `<bind key="d" control="right"></bind>
`       `<bind key="pgup" control="zoom_in"></bind>
`       `<bind key="x" control="zoom_in"></bind>
`       `<bind key="mouse_wheel_up" control="zoom_in"></bind>
`       `<bind key="pgdn" control="zoom_out"></bind>
`       `<bind key="z" control="zoom_out"></bind>
`       `<bind key="mouse_wheel_down" control="zoom_out"></bind>
`       `<bind key="enter" control="enter_exit"></bind>
`       `<bind key="v" control="change_camera"></bind>
`       `<bind key="home" control="change_camera"></bind>
`       `<bind key="space" control="jump"></bind>
`       `<bind key="lshift" control="sprint"></bind>
`       `<bind key="mouse3" control="look_behind"></bind>
`       `<bind key="c" control="crouch"></bind>
`       `<bind key="tab" control="action"></bind>
`       `<bind key="lalt" control="walk"></bind>
`       `<bind key="rctrl" control="vehicle_fire"></bind>
`       `<bind key="lalt" control="vehicle_fire"></bind>
`       `<bind key="mouse1" control="vehicle_fire"></bind>
`       `<bind key="lctrl" control="vehicle_secondary_fire"></bind>
`       `<bind key="num_0" control="vehicle_secondary_fire"></bind>
`       `<bind key="a" control="vehicle_left"></bind>
`       `<bind key="arrow_l" control="vehicle_left"></bind>
`       `<bind key="d" control="vehicle_right"></bind>
`       `<bind key="arrow_r" control="vehicle_right"></bind>
`       `<bind key="arrow_u" control="steer_forward"></bind>
`       `<bind key="arrow_d" control="steer_back"></bind>
`       `<bind key="w" control="accelerate"></bind>
`       `<bind key="s" control="brake_reverse"></bind>
`       `<bind key="x" control="radio_next"></bind>
`       `<bind key="z" control="radio_previous"></bind>
`       `<bind key="F5" control="radio_user_track_skip"></bind>
`       `<bind key="h" control="horn"></bind>
`       `<bind key="2" control="sub_mission"></bind>
`       `<bind key="num_add" control="sub_mission"></bind>
`       `<bind key="space" control="handbrake"></bind>
`       `<bind key="rctrl" control="handbrake"></bind>
`       `<bind key="q" control="vehicle_look_left"></bind>
`       `<bind key="e" control="vehicle_look_right"></bind>
`       `<bind key="mouse3" control="vehicle_look_behind"></bind>
`       `<bind key="mouse2" control="vehicle_mouse_look"></bind>
`       `<bind key="num_4" control="special_control_left"></bind>
`       `<bind key="num_6" control="special_control_right"></bind>
`       `<bind key="num_2" control="special_control_down"></bind>
`       `<bind key="end" control="special_control_down"></bind>
`       `<bind key="num_8" control="special_control_up"></bind>
`       `<bind key="delete" control="special_control_up"></bind>
`       `<bind key="delete" control="aim_weapon"></bind>
`       `<bind key="capslock" control="aim_weapon"></bind>
`       `<bind key="mouse2" control="aim_weapon"></bind>
`       `<bind key="y" control="conversation_yes"></bind>
`       `<bind key="n" control="conversation_no"></bind>
`       `<bind key="g" control="group_control_forwards"></bind>
`       `<bind key="h" control="group_control_back"></bind>
`       `<bind key="g" state="down" command="enter_passenger" arguments=""></bind>
`       `<bind key="t" state="down" command="chatbox" arguments="chatboxsay"></bind>
`       `<bind key="y" state="down" command="chatbox" arguments="teamsay 255 0 0"></bind>
`       `<bind key="F11" state="down" command="radar" arguments="-1"></bind>
`       `<bind key="num_add" state="down" command="radar_zoom_in" arguments=""></bind>
`       `<bind key="num_sub" state="down" command="radar_zoom_out" arguments=""></bind>
`       `<bind key="num_8" state="down" command="radar_move_north" arguments=""></bind>
`       `<bind key="num_2" state="down" command="radar_move_south" arguments=""></bind>
`       `<bind key="num_6" state="down" command="radar_move_east" arguments=""></bind>
`       `<bind key="num_4" state="down" command="radar_move_west" arguments=""></bind>
`       `<bind key="num_0" state="down" command="radar_attach" arguments=""></bind>
`       `<bind key="z" state="down" command="voiceptt" arguments="1"></bind>
`       `<bind key="z" state="up" command="voiceptt" arguments="0"></bind>
`       `<bind key="pgup" state="down" command="chatscrollup" arguments="1"></bind>
`       `<bind key="pgup" state="up" command="chatscrollup" arguments="0"></bind>
`       `<bind key="pgdn" state="down" command="chatscrolldown" arguments="-1"></bind>
`       `<bind key="pgdn" state="up" command="chatscrolldown" arguments="0"></bind>
`       `<bind key="pgup" state="down" command="debugscrollup" arguments="1"></bind>
`       `<bind key="pgup" state="up" command="debugscrollup" arguments="0"></bind>
`       `<bind key="pgdn" state="down" command="debugscrolldown" arguments="-1"></bind>
`       `<bind key="pgdn" state="up" command="debugscrolldown" arguments="0"></bind>
`       `<bind key="num_div" state="down" command="radar_opacity_down" arguments=""></bind>
`       `<bind key="num_mul" state="down" command="radar_opacity_up" arguments=""></bind>
`       `<bind key="num_1" state="down" command="radar_help" arguments=""></bind>
`       `<bind key="F12" state="down" command="screenshot" arguments=""></bind>
`   `</binds>
`   `<updater>
`       `<var>
`           `<version_lastchecktime>`2012-08-31 23:36:44`</version_lastchecktime>
`           `<master_lastchecktime>`2012-08-31 23:36:43`</master_lastchecktime>
`           `<master_highestnotifyrevision>`2011-c-09-02`</master_highestnotifyrevision>
`           `<news_lastchecktime>`2012-08-31 23:36:44`</news_lastchecktime>
`           `<news_lastnewsdate>`2012-01-24`</news_lastnewsdate>
`           `<crashdump_historylist>
`           `</crashdump_historylist>
`       `</var>
`       `<mastercache>
`           `<master>
`               `<revision>`2012-05-09`</revision>
`               `<serverlist>
`                   `<server>[`http://updatesa.mtasa.com/sa/master/?v=%VERSION%&id=%ID%`](http://updatesa.mtasa.com/sa/master/?v=%VERSION%&id=%ID%)</server>
`                   `<server>[`http://updatesa.multitheftauto.com/sa/master/?v=%VERSION%&id=%ID%`](http://updatesa.multitheftauto.com/sa/master/?v=%VERSION%&id=%ID%)</server>
`               `</serverlist>
`               `<interval>`12h`</interval>
`           `</master>
`           `<version>
`               `<serverlist>
`                   `<server priority="3">[`http://updatesa.mtasa.com/sa/version/?v=%VERSION%&id=%ID%&ty=%TYPE%&da=%DATA%&be=%BETA%&re=%REFER%`](http://updatesa.mtasa.com/sa/version/?v=%VERSION%&id=%ID%&ty=%TYPE%&da=%DATA%&be=%BETA%&re=%REFER%)</server>
`                   `<server priority="4">[`http://updatesa.multitheftauto.com/sa/version/?v=%VERSION%&id=%ID%&ty=%TYPE%&da=%DATA%&be=%BETA%&re=%REFER%`](http://updatesa.multitheftauto.com/sa/version/?v=%VERSION%&id=%ID%&ty=%TYPE%&da=%DATA%&be=%BETA%&re=%REFER%)</server>
`               `</serverlist>
`               `<interval>`12h`</interval>
`           `</version>
`           `<report>
`               `<serverlist>
`                   `<server>[`http://updatesa.mtasa.com/sa/report/?v=%VERSION%&id=%ID%`](http://updatesa.mtasa.com/sa/report/?v=%VERSION%&id=%ID%)</server>
`                   `<server>[`http://updatesa.multitheftauto.com/sa/report/?v=%VERSION%&id=%ID%`](http://updatesa.multitheftauto.com/sa/report/?v=%VERSION%&id=%ID%)</server>
`               `</serverlist>
`               `<interval>`12h`</interval>
`               `<filter2>`+all,-{1000~2007},-2050,-2051,-{3120},-{3211},-{4002},-5132,-5133,-5809,-7011,-7106,-7801,-7043,-7050,-7051,-7420,-7601,-{7842~7845},-7940`</filter2>
`               `<minsize>`11`</minsize>
`               `<maxsize>`4001`</maxsize>
`           `</report>
`           `<crashdump>
`               `<serverlist>
`                   `<server priority="3">[`http://updatesa.mtasa.com/sa/crashdump/?v=%VERSION%&id=%ID%&file=%FILE%`](http://updatesa.mtasa.com/sa/crashdump/?v=%VERSION%&id=%ID%&file=%FILE%)</server>
`                   `<server priority="4">[`http://updatesa.multitheftauto.com/sa/crashdump/?v=%VERSION%&id=%ID%&file=%FILE%`](http://updatesa.multitheftauto.com/sa/crashdump/?v=%VERSION%&id=%ID%&file=%FILE%)</server>
`               `</serverlist>
`               `<duplicates>`0`</duplicates>
`               `<maxhistorylength>`100`</maxhistorylength>
`           `</crashdump>
`           `<gtadatafiles>
`               `<serverlist>
`                   `<server priority="3">[`http://updatesa.mtasa.com/sa/gtadatafiles/?v=%VERSION%&id=%ID%`](http://updatesa.mtasa.com/sa/gtadatafiles/?v=%VERSION%&id=%ID%)</server>
`                   `<server priority="4">[`http://updatesa.multitheftauto.com/sa/gtadatafiles/?v=%VERSION%&id=%ID%`](http://updatesa.multitheftauto.com/sa/gtadatafiles/?v=%VERSION%&id=%ID%)</server>
`               `</serverlist>
`           `</gtadatafiles>
`           `<gtadatafiles2>
`               `<serverlist>
`                   `<server priority="3">[`http://updatesa.mtasa.com/sa/gtadatafiles2/?v=%VERSION%&id=%ID%`](http://updatesa.mtasa.com/sa/gtadatafiles2/?v=%VERSION%&id=%ID%)</server>
`               `</serverlist>
`           `</gtadatafiles2>
`           `<trouble>
`               `<serverlist>
`                   `<server>[`http://updatesa.multitheftauto.com/sa/trouble/?v=%VERSION%&id=%ID%&tr=%TROUBLE%`](http://updatesa.multitheftauto.com/sa/trouble/?v=%VERSION%&id=%ID%&tr=%TROUBLE%)</server>
`               `</serverlist>
`           `</trouble>
`           `<ase>
`               `<serverlist>
`                   `<server priority="3">[`http://master.multitheftauto.com/ase/mta/?v=%VERSION%&id=%ID%`](http://master.multitheftauto.com/ase/mta/?v=%VERSION%&id=%ID%)</server>
`                   `<server priority="3">[`http://178.21.18.248/ase2.dat`](http://178.21.18.248/ase2.dat)</server>
`                   `<server priority="4">[`http://1mgg.com/affil/mta`](http://1mgg.com/affil/mta)</server>
`               `</serverlist>
`           `</ase>
`           `<sidegrade>
`               `<serverlist>
`                   `<server priority="3">[`http://updatesa.mtasa.com/sa/sidegrade/?v=%VERSION%&id=%ID%&be=%BETA%&re=%REFER%&wv=%WANTVER%`](http://updatesa.mtasa.com/sa/sidegrade/?v=%VERSION%&id=%ID%&be=%BETA%&re=%REFER%&wv=%WANTVER%)</server>
`                   `<server priority="4">[`http://updatesa.multitheftauto.com/sa/sidegrade/?v=%VERSION%&id=%ID%&be=%BETA%&re=%REFER%&wv=%WANTVER%`](http://updatesa.multitheftauto.com/sa/sidegrade/?v=%VERSION%&id=%ID%&be=%BETA%&re=%REFER%&wv=%WANTVER%)</server>
`               `</serverlist>
`               `<nobrowselist>
`                   `<nobrowse version="1.0">`1.1n;1.1N;1.2n;1.2sx;1.3n;1.3v;`</nobrowse>
`                   `<nobrowse version="1.1">`1.1n;1.1N;1.2n;1.2sx;1.3n;1.3v;`</nobrowse>
`               `</nobrowselist>
`               `<onlybrowselist>
`                   `<onlybrowse version="1.1">`1.3;1.2;1.1;1.0`</onlybrowse>
`                   `<onlybrowse version="1.2">`1.3;1.2;1.1;1.0`</onlybrowse>
`                   `<onlybrowse version="1.3">`1.3;1.2;1.1;1.0`</onlybrowse>
`               `</onlybrowselist>
`           `</sidegrade>
`           `<news>
`               `<serverlist>
`                   `<server priority="3">[`http://updatesa.multitheftauto.com/sa/news/?v=%VERSION%&id=%ID%&be=%BETA%&ln=%LASTNEWS%`](http://updatesa.multitheftauto.com/sa/news/?v=%VERSION%&id=%ID%&be=%BETA%&ln=%LASTNEWS%)</server>
`                   `<server priority="4">[`http://updatesa.mtasa.com/sa/news/?v=%VERSION%&id=%ID%&be=%BETA%&ln=%LASTNEWS%`](http://updatesa.mtasa.com/sa/news/?v=%VERSION%&id=%ID%&be=%BETA%&ln=%LASTNEWS%)</server>
`               `</serverlist>
`               `<interval>`12h`</interval>
`               `<oldestpost>`2010-11-02`</oldestpost>
`               `<maxhistorylength>`3`</maxhistorylength>
`           `</news>
`           `<misc>
`               `<debug>
`                   `<filter2>`-all,+{500~2000}`</filter2>
`               `</debug>
`           `</misc>
`       `</mastercache>
`   `</updater>
`   `<serverbrowser_options>
`       `<list id="0" include_empty="1" include_full="1" include_locked="1"></list>
`       `<list id="1" include_empty="1" include_full="1" include_locked="1" active="1"></list>
`       `<list id="2" include_empty="1" include_full="1" include_locked="1" include_offline="1"></list>
`       `<list id="3" include_empty="1" include_full="1" include_locked="1" include_offline="1"></list>
`   `</serverbrowser_options>
`   `<recently_played_servers>
`   `</recently_played_servers>
`   `<connect_history>
`   `</connect_history>
`   `<server_passwords>
`   `</server_passwords>
`   `<favourite_servers></favourite_servers>

</mainconfig> |lang=“xml”}}

</section>
See Also
--------

[Key names](/docs/Key_names.md "wikilink")
[Control names](/docs/Control_names.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")
