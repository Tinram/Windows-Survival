
# Windows Survival

#### Survival snippets for development on Windows.

#### Developing on Windows? No!

With my every body cell bristling these days at the maligned OS, unfortunately I am sometimes forced by on-site work to use Windows.

The following is a quick reference of mostly common snippets to make a Windows workflow somewhat more bearable.


## Active Directory

Corporate environments love Active Directory (AD). AD will probably harvest your files from *My Documents* and add to a remote network server.  Which for PC roaming access is probably what you want, or perhaps not?

If not, move your personal files to e.g. `C:/mydocs`

-- which will rely on your backup schedule, not AD's (not that I found AD's reliable anyway).


## Clean Windows

+ CCleaner

+ `C:\Users\<username>\AppData\Roaming\`

+ `C:\Users\<pc_name>\AppData\Roaming\Skype\<skype_name>\xxxx-journal`

+ `putty -cleanup` (wipe session data)


## Command-line

For a usable terminal window on Windows < 10:

        mode con cols=140

change encoding:

        chcp 650001        Unicode
        chcp 1252          Latin 1

#### Open in current folder:

+ current directory (nothing selected) > `Shift` + right click > *Open command window here*

#### Registry hack:

+ `HKEY_LOCAL_MACHINE\Software\Classes\Folder\Shell\`
+ create new key called `Command Prompt`
+ default value: `cmd`
+ create new key below `Command Prompt` called `Command`
+ default value: `cmd.exe /k "pushd %L"`


### Commands

#### a few network and file commands

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
`netstat` | network stats | `-a` all, `-b` exes, `-o` owner, `-p` TCP, `-r` routing, `-s` stats, `netstat -an | findstr listening` |
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


## /dev/null

*bitbucket* with *p* = program:

        p > nul
        p 2> nul             err to nul
        p > nul 2>&1         err + out
        p >f 2> nul          out to file, suppress err
        (p) > f 2> nul       out to file, suppress cmd.exe err


## Editors

*not going there ...*

Just don't use Windows Notepad with one level of undo and no recognition of non-CRLF line endings.  (Probably fine on Windows 1.0 in 1985.)


## Diff Folders

        ROBOCOPY cmp cmp2 /e /l /ns /njs /njh /ndl /fp /log:diff.txt


## Drive Mapping

        \\10.0.0.147

in Windows Explorer


## Essential Programs

+ **Git for Windows**
    + not just for *Git*, but for what ships with it:
        + *curl*
        + *grep*
        + *gpg*
        + *md5sum*
        + *shred*

+ **7-zip**
+ **CherryTree**
+ diff program (**CSDiff**, Winmerge etc)
+ password vault (**KeepassX**)
+ PDF viewer (**SumatraPDF**)
+ **ptimer**
+ **PuTTY**
+ **WinSCP**

For standalone programs, add to `C:/<directory>`, and add this directory to *$PATH*, so the programs are available on the terminal from any location.


## File Exchange

**the hard way**

*(else use a local server, network storage, or even online storage to transfer)*

### Win 7

+ *Network and Sharing Center*, enable:
    + network discovery
    + file and printer sharing
    + public folder sharing

### Win XP

+ `services.msc` > required: *Server*, *Computer Browser*
+ Firewall > exceptions > *File and Printer Sharing* > enable


## Keys

### Windows Key +

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


### others

keys | purpose |
---- | ---- |
`Shift` + `right click` | open terminal |
`F2` | rename |
`F3` | search |
`F5` | refresh
`Alt` + `TAB` | cycle windows |
`Alt` + `Shift` + `TAB` | cycle backwards |
`Ctrl` + `Shift` + `ESC` | taskmanager |


## Hosts

        C:\windows\system32\drivers\etc\hosts

create shortcut:

+ `notepad /A <path>`
+ open as administrator


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


## Passwords

        rundll32.exe keymgr.dll,KRShowKeyMgr


## Power Configuration

        HKEY_CURRENT_USER\Control Panel\PowerCfg
    CurrentPowerPolicy
        0   home office
        3   always on
        4   minimal mgt

## Program Installation

(theoretical, Windows often doesn't care)

        \Program Files x86\     x32
        \Program Files\         x64

## sendto

     %APPDATA%\Microsoft\Windows\SendTo

or

`Run` > `shell:sendto`


## Servers

+ [WAMP](http://www.wampserver.com/en/)
    + x64, x32, multiple PHP versions

+ [XAMPP](https://www.apachefriends.org/download.html)
    + x32

### IIS Conflict

Kill IIS when it stops WAMP/XAMPP:

+ Control Panel > Admin Tools > IIS Manager > stop
+ `services.msc` > *Web Deployment Agent Service* > manual start


## Services

+ DCOM Server Process Launcher - defragging
+ Diagnostics Tracking Service - telemetry


## Start Batch

+ add program locations to *$PATH*

*start.bat*

        @echo off
        start cherrytree.exe
        start firefox.exe
        exit


## Taskbar

### Thumbnail Preview Disable

+ `gpedit.msc` > User Configuration > Administrative Templates > Start Menu and Taskbar > *Turn off taskbar thumbnails* > Disabled

+ `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` >
new DWORD > ExtendedUIHoverTime > 30000

*disabled in Creators update*

## Telemetry

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

+ `services.msc` > stop *WindowsUpdate*
+ `C:\Windows\` > rename `SoftwareDistribution` directory
+ `services.msc` > start *WindowsUpdate*


## Windows

### Gone Offscreen

+ right click window on taskbar, or select it and use `Alt + Space`
+ if `Restore'` option available, select it to pop window out of minimised/maximised state
+ `Move` option
+ cursor
+ move mouse


## Windows Explorer

### Kill + Reboot

        taskkill /f /im explorer.exe
        start explorer.exe
