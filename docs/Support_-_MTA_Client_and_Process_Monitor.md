Instructions for generating a process log for MTA:SA Client
-----------------------------------------------------------

### 1. Download Process Monitor from here: <http://technet.microsoft.com/en-us/sysinternals/bb896645>

[frame|center](/File:Client_pm_1.jpg.md "wikilink")

<hr/>
### 2. Unzip ProcessMonitor.zip

<hr/>
### 3. Download <http://nightly.mtasa.com/files/ProcmonMTAConfiguration.pmc> and put it into the Process Monitor directory

[frame|center](/File:Client_pm_2.jpg.md "wikilink")

<hr/>
### 4. Start Procmon.exe (if it starts with a window called 'Process Monitor Filter', press OK to close it).

### Then select the menu item **'File**-&gt;**Import Configuration**'

(If you can't select 'Import Configuration', try running Procmon.exe as administrator) [frame|center](/File:Client_pm_3.jpg.md "wikilink")

<hr/>
### 5. Select the **'ProcmonMTAConfiguration.pmc**' file and press **'Open**'

<hr/>
### 6. Now start MTA and get to the problem

<hr/>
### 7. After problem has occurred, go back to the Process Monitor window and select the menu item **'File**-&gt;**Save...**'

[frame|center](/File:Client_pm_4.jpg.md "wikilink")

<hr/>
### 8. Press the **'Ok**' button in the next window

<hr/>
### 9. Find the file **'Logfile.PML**' and upload at <http://upload.mtasa.com/>

(Give the resulting file link to an MTA developer, or post it on the relevant forum topic) [frame|center](/File:Client_pm_5.jpg.md "wikilink")
