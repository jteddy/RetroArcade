# GroovyMame Setup on Windows10 with CRT Emudriver 2.0/VmMaker

I've installed [GroovyArcade](http://forum.arcadecontrols.com/index.php/topic,160023.0.html) on my 31kHz cabinet and now have [Fightcade2](https://www.fightcade.com/) working on it. It was time to test Windows 10 to see how it performs. By using Windows 10 the idea is to be able to run  other games. Let's see how this performs.

## Windows 10 Installation

You can find a guide on how to create a USB boot key and install Windows 10. 

- Keep your ethernet/wifi disconnected throughout the installation
- Create a local account. Do not create a password.

## Windows 10 Post Configuration

1. Find the MAC address of your card and give your machine a static DHCP address. 
2. Enable remote desktop

   1. Just search for *remote desktop settings*
   2. Move the slider to allow it
3. Enable RDP with a blank password

   1. Click Start, point to Run, type gpedit.msc
   2. Open Computer Configuration\**Windows** Settings\Security Settings\Local Policies\Security Options\Accounts: Limit local account use of blank passwords to console logon only.
   3. Double-click Limit local account use of blank passwords to console logon only.
   4. Click Disabled, and then click OK.
   5. Quit Group Policy Editor.
4. Go to [Ninite](https://ninite.com/) and install some required packages

   1. Chrome
2. Z-Zip
   3. VLC
4. Notepad++
   5. WinSCP
6. Filezilla
   7. Putty
8. .Net 4.8
   9. SumatraPDF
10. Revo
5. Create a directory called arcade to be your root directory
6. Enable file sharing on the directory. I give everyone full control

Note: Do I need to block AMD driver updates?



## Installation

1. Download the latest [GroovyMAME](http://forum.arcadecontrols.com/index.php?topic=151459.0). The files can be found [here](https://drive.google.com/drive/folders/0B5iMjDor3P__aEFpcVNkVW5jbEE?resourcekey=0-fbQO4r4i1aZs4Gf4u3wGWA).

2. Download the matching MAME version. At this time you need to download a [previous version of MAME](https://www.mamedev.org/oldrel.html).

3. Extract GroovyMAME

4. Rename and move extracted directory to your preferred location

5. A file with the name *mame64.exe* should be there. Right-click it, go to Properties, Compatibility and give it Admin. privileges

6. Make sure the following folders are there: *C:\GROOVYMAME\ini* and *C:\GROOVYMAME\ini\source*. The former will be the folder to place per-game (*per-machine*, in the case of home systems) INI configuration files, while the latter will host per-driver INI configuration files. These INI files will only be needed when we want specific MAME settings for a game or group of games, since they'll get priority over Groovy MAME's main configuration file *mame.ini*. Remember this.

7. If it's not present after the extraction, create *mame.ini*: execute 

   ```
   C:\arcade\groovymame\mame64 -cc
   ```

8. Download [CRTEmuDriver](https://geedorah.com/eiusdemmodi/forum/viewtopic.php?id=295).

   1. For my 5550 I chose - [CRT Emudriver & CRT Tools 2.0 beta 15 (Crimson 16.2.1 non-GCN* cards) for Windows 7/8/10 64-bits](https://drive.google.com/file/d/1dwjXRFdySz4moxGTGcVWLdQDG-zw5-cJ/view)

9. It is recommended to follow [Calamity's guide here](https://geedorah.com/eiusdemmodi/forum/viewtopic.php?pid=1052#p1052).

10. Extract CRT_emudriver

11. Rename the folder to make it simpler. I use "CRTEmuDriver"

12. 

