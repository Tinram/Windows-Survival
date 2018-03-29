
# Windows Survival

#### Survival snippets for development on Windows.

#### Developing on Windows?! *No!*

Despite every body cell screaming in the vicinity of the decadent OS, unfortunately I am sometimes forced by on-site work to use Windows.

The following is my quick reference to ease the pain of Windows.

----

#### [Active Directory](#ad)
#### [Clean-up](#cu)
#### [Command-Line](#cl)
#### [Commands](#cs)
#### [/dev/null](#dn)
#### [Editors](#ed)
#### [Diff Folders](#df)
#### [Drive Mapping](#dm)
#### [Essential Programs](#ep)
#### [File Transfer](#ft)
#### [Keys](#ks)
#### [Hosts](#hs)
#### [.msc](#mc)
#### [Passwords](#pw)
#### [Power Configuration](#pc)
#### [Program Installation Folders](#pf)
#### [sendto](#st)
#### [Servers](#sv)
#### [Services](#sc)
#### [Start Batch](#sb)
#### [Taskbar](#tb)
#### [Telemetry](#tm)
#### [Updates](#ud)
#### [Windows](#wd)
#### [Windows Explorer](#we)


----


<a id="ad"></a>
## Active Directory

Corporate environments love Active Directory (AD). I don't.

AD will probably silently harvest files from *My Documents* and add them to some remote network server(s).

For corporate PC roaming access you will probably want this, else you might not.

If not, move personal files out of *My Documents* to another location, such as `C:/mydocs`

-- which will then rely on your backup schedule, not AD's (not that I found AD's consistent anyway).


<a id="cu"></a>
## Clean-up

+ [CCleaner](https://www.ccleaner.com/ccleaner/download)

+ `C:\Users\<username>\AppData\Roaming\`

+ `C:\Users\<username>\AppData\Roaming\Skype\<skype_name>\xxxx-journal`

+ `putty -cleanup` (wipe session data)


<a id="cl"></a>
## Command-Line

For a usable terminal window on Windows < 10

        mode con cols=140

Change encoding:

        chcp 650001        Unicode
        chcp 1252          Latin 1

#### Open terminal in current folder:

+ current directory (nothing selected) > `Shift` + `right click` > *Open command window here*

#### Registry hack:

+ *Run* > `regedit`
+ `HKEY_LOCAL_MACHINE\Software\Classes\Folder\Shell\`
+ create new key called `Command Prompt`
+ default value: `cmd`
+ create new key below `Command Prompt` called `Command`
+ default value: `cmd.exe /k "pushd %L"`


<a id="cs"></a>
### Commands

#### A few network and file commands.

command | description | |
---- | ---- | ---- |
`comp` | compare two files | |
`fc` | file contents compare | |
`find` | text string in file | `/n` line nums, `/c` line count |
`findstr` | string search in file | `findstr /si password *.txt` |
`fsutil` | file utils | `fsutil file createnew <f> 1024` null chars |
`getmac` | MAC address | |
`hostname` | | |
`ipconfig` | IPs | |
`mstsc` | RDP | |
`net` | network info | |
`netsh` | netshell | `netsh interface ip set address local dhcp` |
`netstat` | network stats | `-a` all, `-b` exes, `-o` owner, `-p` TCP, `-r` routing, `-s` stats |
`net use` | network connections | |
`path` | search path | |
`ping` | | |
`ren` | rename | |
`route` | routing table | |
`sort` | sort text | `-r` reverse |
`start` | exe or cmd | |
`systeminfo` | | |
`taskkill` | | |
`tracert` | | |
`tree` | dirs | `tree /F /A` |
`type` | view text file | |
`where` | file locator | |
`xcopy` | | |


<a id="dn"></a>
## /dev/null

**A bitbucket**

*p* = program

        p > nul
        p 2> nul             error to nul
        p > nul 2>&1         error + out
        p >f 2> nul          out to file, suppress error
        (p) > f 2> nul       out to file, suppress cmd.exe error


<a id="ed"></a>
## Editors

*Not going there ...*

Just don't use Windows Notepad, which has one level of undo and no recognition of non-`CRLF` line endings.  (Probably just fine on Windows 1.0 in 1985.)


<a id="df"></a>
## Diff Folders

        ROBOCOPY cmp cmp2 /e /l /ns /njs /njh /ndl /fp /log:diff.txt


<a id="dm"></a>
## Drive Mapping

        \\10.0.0.147


<a id="ep"></a>
## Essential Programs

+ **[Git](https://git-scm.com/download/win)**
    + not just for *Git*, but for what ships with it:
        + *curl*
        + *gpg*
        + *grep*
        + *md5sum*
        + *openssl*
        + *shred*
        + *ssh*

+ **[7-Zip](https://www.7-zip.org/)**
+ **[CherryTree](https://www.giuspen.com/cherrytree/)**
+ diff program (**CSDiff**, WinMerge etc)
+ password vault (**[KeepassX](https://www.keepassx.org/downloads)**)
+ PDF viewer (**[SumatraPDF](https://www.sumatrapdfreader.org/free-pdf-reader.html)**)
+ **[ptime](http://pc-tools.net/win32/ptime/)**
+ **[PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)**
+ **[WinSCP](https://winscp.net/eng/index.php)**

### Standalone Programs

Add standalone programs to `C:/<directory>`, and add this directory location to *$PATH*, so the programs are available on the command-line from any location.


<a id="ft"></a>
## File Transfer

**Easy Way**

+ local server upload, *netcat*, network storage, online storage ...

**Hard Way**

### Win 7

+ *Network and Sharing Center*, enable:
    + network discovery
    + file and printer sharing
    + public folder sharing

### Win XP

+ *Run* > `services.msc` > *Server*, *Computer Browser* (required)
+ Firewall > exceptions > *File and Printer Sharing* > enable


<a id="ks"></a>
## Keys

### Windows Key + ...

keys | purpose |
---- | ---- |
`Alt` + `PrtScrn` | screenshot of active window |
`Break` | system properties |
`E` | Explorer |
`F3` | file search |
`L` | lock |
`M` | minimise windows |
`P` | projector |
`R` | run |
`R` | > `Ctrl` + `Shift` + `Enter` = admin |
`Shift` + `L-Alt` + `PrtScrn` | high contrast |


### Others

keys | purpose |
---- | ---- |
`Shift` + `right click` | open terminal |
`F2` | rename |
`F3` | search |
`F5` | refresh
`Alt` + `TAB` | cycle windows |
`Alt` + `Shift` + `TAB` | cycle backwards |
`Ctrl` + `Shift` + `ESC` | taskmanager |


<a id="hs"></a>
## Hosts

        C:\windows\system32\drivers\etc\hosts

Create shortcut:

+ *Run* > `notepad /A <path>`
+ `right click` > *Run as administrator*


<a id="mc"></a>
## .msc

.msc | description |
---- | ---- |
`compmgmt.msc` | computer management |
`devmgmt.msc` | device manager |
`diskmgmt.msc` | disk manager |
`eventvwr.msc`| event viewer |
`fsmgmt.msc` | shared folders |
`gpedit.msc` | group policy |
`lusrmgr.msc` | local users / groups |
`ntmsmgr.msc` | removable storage |
`ntmsoprq.msc` | " |
`perfmon.msc` | performance |
`secpol.msc` | security |
`services.msc` | services |
`wf.msc` | firewall |
`wmimgmt.msc` | WMI |

----

.cpl | description |
---- | ---- |
`nusrmgr.cpl` | user accounts |
`firewall.cpl` | |


<a id="pw"></a>
## Passwords

*Run* > `rundll32.exe keymgr.dll,KRShowKeyMgr`


<a id="pc"></a>
## Power Configuration

*Run* > `regedit`

        HKEY_CURRENT_USER\Control Panel\PowerCfg > CurrentPowerPolicy
            0  home office
            3  always on
            4  minimal management

<a id="pf"></a>
## Program Installation Folders

(theoretical, Windows often doesn't care)

        \Program Files (x86)\     x32
        \Program Files\           x64


<a id="st"></a>
## sendto

     %APPDATA%\Microsoft\Windows\SendTo

or

*Run* > `shell:sendto`


<a id="sv"></a>
## Servers

+ [WAMP](http://www.wampserver.com/en/)
    + x64, x32, multiple PHP versions

+ [XAMPP](https://www.apachefriends.org/download.html)
    + x32

### IIS Conflict

Kill IIS when it stops WAMP / XAMPP:

+ Control Panel > Admin Tools > IIS Manager > stop
+ *Run* > `services.msc` > *Web Deployment Agent Service* > *manual start*


<a id="sc"></a>
## Services

+ DCOM Server Process Launcher - defragging
+ Diagnostics Tracking Service - telemetry


<a id="sb"></a>
## Start Batch

1. *start.bat*

        @echo off
        start cherrytree.exe
        start firefox.exe
        exit

2. add the program locations in *start.bat* to *$PATH*


<a id="tb"></a>
## Taskbar

### Thumbnail Preview Disable

+ *Run* > `gpedit.msc` > User Configuration > Administrative Templates > Start Menu and Taskbar > *Turn off taskbar thumbnails* > Disabled

+ `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` >
new DWORD > ExtendedUIHoverTime > 30000

*both disabled by Creators update ... sigh*


<a id="tm"></a>
## Telemetry

### Win 10

+ Start > Settings > Privacy
    + disable as many as possible, *especially* **Inking**

#### Disable Services

+ DiagTrack
+ Connected User Experience and Telemetry

#### Disable via Registry

        sc delete DiagTrack
        sc delete dmwappushservice
        echo "" > C:\ProgramData\Microsoft\Diagnosis\ETLLogs\AutoLogger\AutoLogger-Diagtrack-Listener.etl
        reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f


<a id="ud"></a>
## Updates

### Win 7 Bad Updates

+ disable Win 10 upgrade path:

        HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate
        DisableOSUpgrade > 1

        HKLM\Software\Microsoft\Windows\CurrentVersion\WindowsUpdate\OSUpgrade
        ReservationsAllowed > 0

+ *KB3133977*, March 2016
    + prevents booting, looks like hard drive failure
    + remedy: disable UEFI secure boot; OS Type > Other OS

### Borked Updates

*Updates jammed / Updates Service disabled error*

+ *Run* > `services.msc` > stop *WindowsUpdate*
+ `C:\Windows\` > rename `SoftwareDistribution` directory
+ *Run* > `services.msc` > start *WindowsUpdate*


<a id="wd"></a>
## Windows

### Unreachable Offscreen

+ `right click` window on taskbar, or select it and use `Alt` + `Space`
+ if `Restore` option available, select it to pop window out of minimised/maximised state
+ `Move`
+ cursor
+ move mouse


<a id="we"></a>
## Windows Explorer

### Kill + Reboot

        taskkill /f /im explorer.exe
        start explorer.exe
