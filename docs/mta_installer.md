Control freaks guide to what the hell MTA does to my computer.
==============================================================

MTA installer does this
-----------------------

### 1. Creates install directory

  
Creates and copies files into the install directory and sets its permssions so MTA can also use it for saving and caching game relevent data.

  
The location can be changed during installation. The default location is:

  
*C:\\Program Files (x86)\\Multi Theft Auto 1.3\\*

### 2. Creates directory

  
Creates this directory and sets its permssions so MTA can use it for storing update files:

  
*C:\\ProgramData\\Multi Theft Auto All\\*

### 3. Creates registry key

  
Creates this registry key and sets its permssions so MTA can use it to store various settings it needs at launch time (ie Location of GTA directory):

  
*HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Multi Theft Auto: San Andreas All*

### 4. Creates registry key

  
Creates this registry key so the uninstaller will show up in Windows uninstall list

  
*HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\MTA:SA 1.3*

### Optional things

#### 5. If 'Create a Start Menu group' is selected during installation

  
Creates this directory so shortcuts will show up in the start menu:

  
*C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\MTA San Andreas 1.3\\*

#### 6. If 'Create a Desktop Shortcut' is selected during installation

  
Creates this file for the desktop icon:

  
*C:\\Users\\Public\\Desktop\\MTA San Andreas 1.3*

#### 7. If 'Register mtasa:// protocol' is selected during installation

  
Creates this registry key so you can click browser links like mtasa://1.2.3.4:123 and launch MTA (chrome doesn't support this howerver):

  
*HKEY\_CLASSES\_ROOT\\mtasa*

#### 8. If 'Add to Windows Games Explorer' is selected during installation (Only relevant for Vista and up)

  
Gets Windows to add MTA to its Game Explorer system

  
*Ask Microsft what this does, because I have no idea.*

*The above assumes 64bit Windows 7 - Different Windows versions will probably use different locations*

MTA Installer FAQ:
------------------

Q. Do I have to uninstall before installing a new MTA version?

  
A. No. The installer will automatically upgrade the old version.

Q. Can I have lots of different installs of MTA

  
A. Yes.
