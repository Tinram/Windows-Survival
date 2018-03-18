
# Windows Survival

#### Survival snippets for development on Windows.

#### Developing on Windows? No!

Despite my every body cell bristling these days when near the maligned OS, unfortunately I am sometimes forced by on-site work to use Windows.

The following is a quick reference of mostly common snippets to make Windows workflow somewhat more bearable.

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


## Active Directory <a id="ad"></a>

Corporate environments love Active Directory (AD).

AD will probably harvest your files from *My Documents* and add them to a remote network server. For PC roaming access you will want this, else you might not.

If not, move your personal files from *My Documents* to another location, such as `C:/mydocs`

-- which will then rely on your backup schedule, not AD's (not that I found AD's that frequent or reliable anyway).


## Clean-up <a id="cu"></a>

+ [CCleaner](https://www.ccleaner.com/ccleaner/download)

+ `C:\Users\<username>\AppData\Roaming\`

+ `C:\Users\<pc_name>\AppData\Roaming\Skype\<skype_name>\xxxx-journal`

+ `putty -cleanup` (wipe session data)


## Command-Line <a id="cl"></a>

For a usable terminal window on Windows < 10

        mode con cols=140

Change encoding:

        chcp 650001        Unicode
        chcp 1252          Latin 1

#### Open in current folder:

+ current directory (nothing selected) > `Shift` + `right click` > *Open command window here*

#### Registry hack:

+ `regedit`
+ `HKEY_LOCAL_MACHINE\Software\Classes\Folder\Shell\`
+ create new key called `Command Prompt`
+ default value: `cmd`
+ create new key below `Command Prompt` called `Command`
+ default value: `cmd.exe /k "pushd %L"`


### Commands <a id="cs"></a>

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


## /dev/null <a id="dn"></a>

**A bitbucket**

*p* = program

        p > nul
        p 2> nul             error to nul
        p > nul 2>&1         error + out
        p >f 2> nul          out to file, suppress error
        (p) > f 2> nul       out to file, suppress cmd.exe error


## Editors <a id="ed"></a>

*Not going there ...*

Just don't use Windows Notepad, which has one level of undo and no recognition of non-`CRLF` line endings.  (Probably just fine on Windows 1.0 in 1985.)


## Diff Folders <a id="df"></a>

        ROBOCOPY cmp cmp2 /e /l /ns /njs /njh /ndl /fp /log:diff.txt


## Drive Mapping <a id="dm"></a>

        \\10.0.0.147


## Essential Programs <a id="ep"></a>

+ **Git for Windows**
    + not just for *Git*, but for what ships with it:
        + *curl*
        + *grep*
        + *gpg*
        + *md5sum*
        + *shred*

+ **[7-Zip](https://www.7-zip.org/)**
+ **[CherryTree](https://www.giuspen.com/cherrytree/)**
+ diff program (**CSDiff**, WinMerge etc)
+ password vault (**[KeepassX](https://www.keepassx.org/downloads)**)
+ PDF viewer (**[SumatraPDF](https://www.sumatrapdfreader.org/free-pdf-reader.html)**)
+ **ptimer**
+ **[PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)**
+ **[WinSCP](https://winscp.net/eng/index.php)**

For standalone programs, add to `C:/<directory>`, and add this directory to *$PATH*, so the programs are available on the terminal from any location.


## File Transfer <a id="ft"></a>

**The hard way:**

*(easier way: use local server upload, netcat, network storage, or online storage)*

### Win 7

+ *Network and Sharing Center*, enable:
    + network discovery
    + file and printer sharing
    + public folder sharing

### Win XP

+ `services.msc` > *Server*, *Computer Browser* (required)
+ Firewall > exceptions > *File and Printer Sharing* > enable


## Keys <a id="ks"></a>

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


## Hosts <a id="hs"></a>

        C:\windows\system32\drivers\etc\hosts

Create shortcut:

+ `notepad /A <path>`
+ `right click` > *Run as administrator*


## .msc <a id="mc"></a>

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


## Passwords <a id="pw"></a>

        rundll32.exe keymgr.dll,KRShowKeyMgr


## Power Configuration <a id="pc"></a>

`regedit`

        HKEY_CURRENT_USER\Control Panel\PowerCfg > CurrentPowerPolicy
            0  home office
            3  always on
            4  minimal management

## Program Installation Folders <a id="pf"></a>

(theoretical, Windows often doesn't care)

        \Program Files (x86)\     x32
        \Program Files\           x64

## sendto <a id="st"></a>

     %APPDATA%\Microsoft\Windows\SendTo

or

`Run` > `shell:sendto`


## Servers <a id="sv"></a>

+ [WAMP](http://www.wampserver.com/en/)
    + x64, x32, multiple PHP versions

+ [XAMPP](https://www.apachefriends.org/download.html)
    + x32

### IIS Conflict

Kill IIS when it stops WAMP/XAMPP:

+ Control Panel > Admin Tools > IIS Manager > stop
+ `services.msc` > *Web Deployment Agent Service* > *manual start*


## Services <a id="sc"></a>

+ DCOM Server Process Launcher - defragging
+ Diagnostics Tracking Service - telemetry


## Start Batch <a id="sb"></a>

+ add program locations to *$PATH*

*start.bat*

        @echo off
        start cherrytree.exe
        start firefox.exe
        exit


## Taskbar <a id="tb"></a>

### Thumbnail Preview Disable

+ `gpedit.msc` > User Configuration > Administrative Templates > Start Menu and Taskbar > *Turn off taskbar thumbnails* > Disabled

+ `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` >
new DWORD > ExtendedUIHoverTime > 30000

*disabled in Creators update ...*

## Telemetry <a id="tm"></a>

### Win 10

+ Start > Settings > Privacy
    + disable as many as possible, especially 'inking'

#### Disable Services

+ DiagTrack
+ Connected User Experience and Telemetry

#### Disable via Registry

        sc delete DiagTrack
        sc delete dmwappushservice
        echo "" > C:\ProgramData\Microsoft\Diagnosis\ETLLogs\AutoLogger\AutoLogger-Diagtrack-Listener.etl
        reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f


## Updates <a id="ud"></a>

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

+ `services.msc` > stop *WindowsUpdate*
+ `C:\Windows\` > rename `SoftwareDistribution` directory
+ `services.msc` > start *WindowsUpdate*


## Windows <a id="wd"></a>

### Unreachable Offscreen

+ `right click` window on taskbar, or select it and use `Alt` + `Space`
+ if `Restore` option available, select it to pop window out of minimised/maximised state
+ `Move`
+ cursor
+ move mouse


## Windows Explorer <a id="we"></a>

### Kill + Reboot

        taskkill /f /im explorer.exe
        start explorer.exe
