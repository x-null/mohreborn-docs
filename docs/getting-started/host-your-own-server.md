This guide will take you through installing the Reborn Patch on your MoH:AA Server and
basic configuration.

## Installation

### Linux

!!! warning "MAKE A BACKUP OF YOU ORIGINAL FILES BEFORE INSTALLING THE PATCH"
    It should be enough to backup following files:
    
    - mohaa_lnxded
    - fgameded.so 
    
    But if you are not sure, it's better to make a copy of whole MoH:AA directory.


**Steps**

- Download latest Linux patch version from [HERE](../downloads.md#linux) and unzip it.
- **Make a backup of your existing server**.
  
    There are only a couple of files changed by the patch,
    but if you are not familiar with all the files and folders on your server,
    this can become confusing, so it's safer to backup everything.

- Shut down your MOHAA server via your host in the normal way. If your host has an auto restart feature, ensure your server does not restart after you have stopped it.
- Rename file **fgameded.so** to **fgamededmohaa.so**

    The file will be located in your MOHAA base folder (*for example /opt/MOHAA/*).
    Base game folder location may differ depending on what host you are on.
    Some hosts may provide a HTTP file manager where you can rename the file or use FTP.

- Copy **fgameded.so** file that comes with the patch and paste it into your server's MOHAA base folder.
- Copy all of the rest of files that come with the patch and paste them into your server's MOHAA base folder.
- Hurray! You are done with installing the patch!
 
    It should run without crashing.
    If it crashes, or doesn't start at all, you probably made a mistake during installation process.
    Restore your back-up copy and repeat the installations steps, this time with more caution.

!!! note
    It is important that you keep the original files and just rename them, otherwise the server will not work. 

### Windows

!!! warning "MAKE A BACKUP OF YOU ORIGINAL FILES BEFORE INSTALLING THE PATCH"
    It should be enough to backup following files:
    
    - mohaa_server.exe
    - gamex86.dll
    
    But if you are not sure, it's better to make a copy of whole MoH:AA directory.

**Steps**

- Download latest Windows patch version from [HERE](../downloads.md#windows) and unzip it.
- **Make a backup of your existing server**.
  
    There are only a couple of files changed by the patch,
    but if you are not familiar with all the files and folders on your server,
    this can become confusing, so it's safer to backup everything.

- Shut down your MOHAA server via your host in the normal way. If your host has an auto restart feature, ensure your server does not restart after you have stopped it.
- Rename file **gamex86.dll** to **gamex86mohaa.dll**

    The file will be located in your MOHAA main folder (*for example C:/MOHAA/main*).
    MoHAA main folder location may differ depending on what host you are on.
    Some hosts may provide a HTTP file manager where you can rename the file or use FTP.

- Copy **gamex86.dll** file that comes with the patch and paste it into your server's MoHAA /main/ folder.
- Copy all of the rest of files that come with the patch and paste them into your server's MoHAA /main/ folder.
- Hurray! You are done with installing the patch!
 
    It should run without crashing.
    If it crashes, or doesn't start at all, you probably made a mistake during installation process.
    Restore your back-up copy and repeat the installations steps, this time with more caution.

!!! note
    It is important that you keep the original files and just rename them, otherwise the server will not work. 

### Docker

You can run game server as Docker container. Provided images come with preinstalled Reborn patch and other fixes.
They also include all required OS libraries, so it's super easy to run your server with single command.

#### Linux version

You can use the following pull command to pull the docker image:

```bash
docker pull appelpitje/mohaa-server:AA-Reborn
```

To run a container, you can use:

```bash
docker run -p 12203:12203/udp -p 12300:12300/udp appelpitje/mohaa-server:AA-Reborn
```

#### Windows version

You can use the following pull command to pull the docker image:

```bash
docker pull appelpitje/mohaa-server:AA-Reborn-win32
```

To run a container, you can use:

```bash
docker run -p 12203:12203/udp -p 12300:12300/udp appelpitje/mohaa-server:AA-Reborn-win32
```

### Troubleshooting

If your server crashes after installation, it can be caused by incompatible MoH:AA binary files versions.
You may want to replace them with binaries that are known to be working with the patch.

You can find them and download from [HERE](../downloads.md#compatible-binaries).

If you tried compatible binaries and are still experiencing problems - don't hesitate and contact us using any available
channel (see: [xNULL Community](../index.md#xnull-community)).

## Basic configuration

This is a template for server configuration file, that should let you set up your Reborn Server from scratch in few seconds.

```
// Server Config File Template

// The following 3 commands are usually set on the command line that starts the server
// MOHAA_server.exe +set dedicated 2 +set developer 2 +set logfile 2 +exec server.cfg
seta dedicated "2"  // type of server | 0=listen server, 1=LAN server, 2=internet server
seta logfile "2"    // console logging | 0=no log, 1=buffered, 2=continuous
seta developer "2"  // verbose server logging | 0=off, 1=server, 2=server and client

seta sv_hostname "MoH Reborn"  // server name
seta sv_maxclients "32"        // maximum number of players
seta sv_maxrate "25000"        // server-side limit for the client rate
seta sv_allowdownload "0"      // toggles the ability for clients to download files from the server | default=1
seta sv_timeout "30"           // the amount of time for the server to wait for a client packet before assuming a disconnected state | default=120
seta sv_zombietime "1"         // the amount of time in minutes before a timed out player is removed from the server | default=2
seta sv_runspeed "250"         // running speed | default=250
seta sv_walkspeed "150"        // walking speed | default=150
seta g_allowjointime "10"      // time in secods the player has to spawn when the round starts in objective mode | default=30
seta g_droppeditemlife "30"    // weapons/healthpacks life duration in seconds when dropped | default=30
seta g_forcerespawn "10"       // number of seconds until a player is automatically respawned (if the player doesn't do it by itself) | disabled=0, default=0
seta g_forceteamspectate "1"   // force team only spectating | default=1
seta g_immediateswitch "0"     // faster weapon switch (skips the putaway weapon animation) | 1=enabled, 0=disabled, default=0
seta g_inactivekick "0"        // amount of time in seconds a player can remain inactive before kicked | 0=disabled, default=900
seta g_inactivespectate "0"    // time in seconds to it takes move an afk player to expectator | 0=disabled, default=60
seta g_teamdamage "1"          // toggles team damage | default=0
seta g_voicechat "1"           // toggles character specific pain/death sounds (saves server sound indexes if turned off) | default=1

// Server Passwords
seta rconpassword ""           // password for remote console control of the server
seta password ""               // the serverside password players use to get on the server
seta sv_privateclients "0"     // number of spots, out of sv_maxclients, reserved for players with the server password (sv_privatepassword) | default=0
seta sv_privatepassword ""     // password for private clients to login with

// Voting options
seta g_allowvote "0"           // toggles the voting system | default=1
seta g_votetimeout "0.5"       // sets the Vote-Expire-Time | 1=1 minute, 0.5=30 seconds

// Reborn cvars. More info on mohreborn.com
seta g_badchatlimit "3"        // limit of bad words a player can say on chat before he gets kicked when sv_filterchat is on | default=3
seta g_teambalance "0"         // forces the "Auto Join Team" on new players | default=0
seta sv_antistwh "1"           // toggles the Anti Shoot Through Walls Hack System | default=1
seta sv_antiwh "0"             // toggles the Anti Wallhack System (Broken, it is not recommended to turn it on) | 0=disabled,
seta sv_banning "1"            // toggles the Banning System | default=1
seta sv_disablechat "0"        // disables the server's chat | default=0
seta sv_disabletaunt "0"       // disables taunts for all players on server | default=0
seta sv_filterchat "1"         // toggles the Chat Filtering System | default=1
seta sv_kickbadcmd "0"         // when set to 1, server will kick players using malicious or bad commands | default=1
seta sv_kickping "0"           // when a player ping exceeds this value, he will get kicked from server | 0=disabled, default=500
seta sv_maxconnperip "3"       // maximum connections per IP | -1=disabled, default=3
seta sv_protectnames "1"       // toggles the Name Protection System (protectednamefilter.cfg) | default=1
seta sv_recoilemulation "0"    // toggles the Anti NoRecoil System | default=0
seta sv_stufftextdetection "0" // toggles the Stufftext Bypass Detection System (Broken, it is not recommended to turn it on) | default=1
seta sv_updatedelay "24"       // ammount of hours to wait until next update check | default=12

// Gametype
seta g_gametype "1"  // 1=Free-For-All, 2=Team-Match, 3=Round-Based-Match, 4=Objective-Match
seta timelimit "0"   // amount of minutes before new map loads or next match begins | 0=no limit
seta fraglimit "50"  // sets the fraglimit | 0=no limit
seta roundlimit "0"  // sets the roundlimit in minutes | 0=no limit

seta sv_maplist "dm/mohdm1 dm/mohdm3 dm/mohdm4 dm/mohdm6"

map "dm/mohdm6" // Starts the first map (Stalingrad)
```

## Game hosting services

If you don't feel like renting a VPS or hosting from home 
and want to host your own MoH:AA/SH/BT server without a hassle, you can consider using
game hosting services offered by various companies.

One of our core maintainers - **own3mall**, owns such a company and can host MoH:AA/SH/BT server
for you: [WeBeHostiN](https://webehostin.com/games.php){: target="_blank"}.
